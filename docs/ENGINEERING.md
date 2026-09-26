# Engineering Deep-Dive

[← Back to README](../README.md)

> This document explains the reasoning behind Typly's engine — what each stage does and why it was built that way. Implementation-level detail (exact functions, algorithms, formulas) is intentionally withheld; see [License & Usage](../README.md#license--usage).

---

## Table of Contents

- [Pipeline Overview](#pipeline-overview)
- [1. Audio Capture](#1-audio-capture)
- [2. Chunking & Segmentation](#2-chunking--segmentation)
- [3. Transcription Engine](#3-transcription-engine)
- [4. Overlap-Merge Reconstruction](#4-overlap-merge-reconstruction)
- [5. AI Enhancement Layer](#5-ai-enhancement-layer)
- [6. Output Safety](#6-output-safety)
- [Engineering Decisions Log](#engineering-decisions-log)

---

## Pipeline Overview

Speech goes through six stages between the moment you release the hotkey and the moment text appears at your cursor:

```
🎙️ Capture → ✂️ Chunk → 🧠 Transcribe → 🔗 Merge → ✨ Enhance (optional) → ✅ Safety Check → Output
```

Every stage exists to solve a specific real-world failure mode observed during development — not as a default template.

## 1. Audio Capture

| Spec | Value |
|---|---|
| Mode | Persistent background stream (not started/stopped per recording) |
| Sample rate | 16kHz, mono |
| Activation | Global hotkey hook (Win + Ctrl) |

**Why persistent, not on-demand:** Starting an audio stream from scratch on every hotkey press adds noticeable latency — the first half-second of speech would be clipped. Keeping the stream open in the background means recording starts the instant the hotkey is pressed, with nothing lost.

## 2. Chunking & Segmentation

| Spec | Value |
|---|---|
| Chunk length | 15 seconds |
| Overlap window | 1 second between consecutive chunks |
| Trigger | Voice Activity Detection (VAD) gap threshold |

**Why 15 seconds specifically:** This was a deliberate token-budget decision, not an arbitrary round number. Longer chunks risk exceeding the transcription model's reliable context window (raising hallucination risk near the end of a chunk); shorter chunks multiply the number of chunk-boundary seams that need to be stitched back together cleanly. 15 seconds was the point where both risks were acceptably low in testing.

**Why the overlap:** Without overlap, a word spoken exactly on a chunk boundary gets clipped in half — a real bug observed early in development. The 1-second overlap guarantees any boundary word is fully captured in at least one chunk, at the cost of needing a deduplication step afterward (see §4).

## 3. Transcription Engine

| Spec | Value |
|---|---|
| Decode strategy | Beam search, tuned beam width |
| Fallback | Multi-tier temperature fallback on low-confidence decode |
| Hardware | Automatic NVIDIA GPU detection (`nvidia-smi`-based, no dependency on a specific ML framework's own GPU check) |

**Why a GPU-detection helper instead of relying on a framework's built-in check:** An earlier version depended on a deep-learning framework's own CUDA-availability check, which occasionally misreported GPU presence on certain driver configurations. Querying `nvidia-smi` directly is more reliable and framework-agnostic — it also means CPU-only machines fail predictably into CPU mode instead of crashing.

**Why temperature fallback:** A single fixed decode setting occasionally produces a confidently-wrong transcription on ambiguous audio. A tiered fallback re-attempts decoding with adjusted parameters when the first pass looks unreliable, trading a small amount of extra compute time for meaningfully fewer garbled outputs.

## 4. Overlap-Merge Reconstruction

Because consecutive chunks share a 1-second overlap (§2), the raw transcriptions of adjacent chunks contain duplicate words at the seam. Before the final text is assembled, a phrase-level matching step detects this duplication and merges each pair of chunks into one continuous, non-repeating transcript.

**Why phrase-level, not just exact string matching:** Speech-to-text output isn't always character-identical between two passes over the same overlapping audio (minor variance in punctuation or capitalization at the boundary). Phrase-level matching tolerates that variance while still reliably identifying the true duplicate region.

## 5. AI Enhancement Layer

| Spec | Value |
|---|---|
| Providers supported | 9+ (bring your own API key) |
| Scope | Optional — grammar, tone, and clarity polishing on top of raw transcription |
| Token budgeting | Dynamic, calculated per-request rather than a fixed cap |

**Why dynamic token budgeting:** A fixed output-length cap either wastes budget on short dictations or silently truncates long ones. The budget is calculated from the actual input length so the enhancement step scales proportionally — this was added after discovering that longer dictations were occasionally being cut off mid-sentence under a fixed cap.

**Why enhancement is optional, not mandatory:** Raw transcription must always be usable on its own. If no LLM provider is configured, or a provider call fails, Typly falls back to unmodified transcription rather than blocking output — see [Reliability Philosophy](../README.md#reliability-philosophy).

## 6. Output Safety

A symmetric length-validation check runs on enhanced output before it's returned: both unexpectedly short and unexpectedly long results (relative to the input) are flagged and handled, rather than only guarding against one direction of failure.

**Why symmetric, not one-directional:** An earlier version only checked for truncation (output too short). During testing, a separate failure mode surfaced — enhancement occasionally *expanded* output far beyond the input length in a way that indicated repetition or drift, not real content. Guarding both directions closed that gap.

## Engineering Decisions Log

| Decision | Reason |
|---|---|
| `nvidia-smi`-based GPU detection over framework-native checks | More reliable across driver configurations; framework-agnostic |
| 15-second chunking with 1-second overlap | Balances hallucination risk against seam-stitching complexity |
| Phrase-level overlap merge over exact-match dedup | Tolerates minor transcription variance at chunk boundaries |
| Dynamic token budgeting over fixed caps | Prevents truncation on long dictations without wasting budget on short ones |
| Symmetric output-length safety check | Catches both truncation and abnormal expansion, not just one failure mode |
| AI enhancement kept fully optional | Guarantees a usable result even with no LLM configured or a failed provider call |

---

[← Back to README](../README.md) · [Security Architecture →](SECURITY.md)
