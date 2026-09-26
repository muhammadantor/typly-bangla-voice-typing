<!--
SEO keyword block (not rendered visually, indexed by search & LLM crawlers):
AI voice typing software Windows, Bangla speech to text app, English voice dictation tool, hands-free typing software,
voice to text software Windows, AI transcription app Bangladesh, Windows dictation assistant, Bangla voice recognition AI,
offline voice typing tool, hotkey voice typing Windows, AI-enhanced dictation software, hardware-locked license system,
AutomateIQ Labs, voice typing app Bangladesh, speech recognition desktop application, Bangla English mixed language typing.
-->

<div align="center">

<img src="typly-icon.png" width="120" alt="Typly Icon">

<h1>Typly</h1>
<p><b>AI-Powered Bangla & English Voice Typing for Windows</b></p>

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Languages](https://img.shields.io/badge/Languages-Bangla%20%2B%20English-2E8B57?style=for-the-badge)
![License](https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![Maintained by](https://img.shields.io/badge/Maintained%20by-AutomateIQ%20Labs-black?style=for-the-badge)

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=17&pause=1000&color=2E8B57&center=true&vCenter=true&random=false&width=750&lines=Speak.+It+Types.+Instantly.+%F0%9F%8E%99%EF%B8%8F;Bangla+%2B+English+%2B+Mixed+Mode+%E2%8C%A8%EF%B8%8F;AI-Enhanced+Transcription+%E2%9C%A8;Hardware-Locked+Licensing+%F0%9F%94%92)](https://git.io/typing-svg)

<br/>

**A background voice-typing assistant for Windows — hold a hotkey, speak in Bangla or English, and your words appear instantly wherever your cursor is. Built by AutomateIQ Labs.**

<br/>

> 📌 **This repository is for distribution and documentation only.** It showcases the product, its engineering, and its security model. No source code is published here — see [License & Usage](#license--usage) below.

</div>

**Core keywords:** AI voice typing Windows, Bangla speech-to-text, English voice dictation, hands-free typing tool, voice-to-text software, AI transcription app, Windows dictation assistant, Bangla voice recognition, speech AI Bangladesh, offline voice typing tool.

---

## 📌 Table of Contents

- [Overview](#overview)
- [The Problem It Solves](#the-problem-it-solves)
- [Screenshots](#screenshots)
- [Design Principles](#design-principles)
- [What Makes Typly Different](#what-makes-typly-different)
- [Typly vs. Typical Voice-Typing Tools](#️-typly-vs-typical-voice-typing-tools)
- [Tech Highlights](#tech-highlights)
- [Reliability Philosophy](#reliability-philosophy)
- [Pricing](#pricing)
- [Download](#download)
- [System Requirements](#system-requirements)
- [Good to Know (Not Bugs)](#good-to-know-not-bugs)
- [Documentation](#documentation)
- [FAQ](#faq)
- [About The Builder](#-about-the-builder)
- [License & Usage](#license--usage)
- [Connect](#connect)

---

## Overview

Typly runs quietly in the Windows system tray. Hold **Win + Ctrl**, speak naturally, release — and the transcribed text lands wherever your cursor is, in any app. No recording buttons, no app-switching, no manual file handling. It supports Bangla, English, and mixed-language dictation, with optional AI-powered grammar and tone enhancement on top of the raw transcription.

## The Problem It Solves

Typing is slower than speaking, but most voice-typing tools fall short in real use:

- Built-in OS dictation is usually English-first, with weak or no Bangla support
- Most tools require switching to a dedicated app or window instead of working system-wide
- Raw transcriptions are often grammatically rough and need manual cleanup
- Licensing on most paid tools is easy to bypass, undermining the business model

Typly was engineered specifically around these gaps — system-wide hotkey activation, true dual-language support, optional AI-enhanced output, and a hardware-locked licensing system.

## Screenshots

| Main Screen | License | Plans |
|---|---|---|
| ![Main Screen](main-screen.png) | ![License Screen](license-screen.png) | ![Plans Screen](-plans-screen.png) |

| Payment | Help | System Tray |
|---|---|---|
| ![Payment Popup](payment-popup.png) | ![Help Screen](help-screen.png) | ![System Tray](system-tray.png) |

## Design Principles

- **Never guess silently.** If the engine isn't confident in what it heard, it should never quietly produce garbled or hallucinated text — output correctness is treated as more important than always returning something.
- **Tune, don't assume.** Every timing and chunking parameter was arrived at through iterative testing against real speech patterns, not left at library defaults.
- **Degrade gracefully.** AI enhancement is optional — if no LLM is configured or a provider fails, Typly still returns clean raw transcription rather than failing the whole action.
- **Protect the business model, not just the code.** Licensing is treated as a first-class engineering concern, not an afterthought bolted on at the end.
- **The user should never wonder if it's broken.** Expected behaviors that look like bugs (permission prompts, GPU-only acceleration) are documented plainly instead of left to guesswork.

## What Makes Typly Different

- 🎯 **True system-wide hotkey** — works inside any app, no window focus required
- 🇧🇩🇬🇧 **Real dual-language support** — Bangla, English, and Mixed mode, not just English with poor Bangla accuracy
- 🧠 **Optional AI enhancement layer** — raw transcription can be polished for grammar and tone via 9+ LLM providers (bring your own API key)
- ⚡ **Automatic GPU detection** — uses NVIDIA GPU acceleration when available, falls back cleanly to CPU
- 🔒 **Hardware-locked licensing** — tied to the machine, engineered to resist casual tampering
- 📊 **Live usage visibility** — daily and weekly word usage tracked inside the app, not hidden

## ⚖️ Typly vs. Typical Voice-Typing Tools

| | Typical Voice-Typing Tool | Typly |
|---|---|---|
| **Language support** | Usually English-first, weak or no Bangla | True Bangla + English + Mixed mode |
| **Activation** | App-specific window or manual button | System-wide hotkey, works inside any app |
| **Output quality** | Raw transcription only | Optional AI-enhanced grammar & tone polish |
| **Hardware use** | Often CPU-only or cloud-dependent | Automatic NVIDIA GPU detection, clean CPU fallback |
| **Licensing** | Simple key check, easy to bypass | Multi-layer, hardware-bound validation |
| **Offline capability** | Often requires constant internet | Fully offline after the one-time model download |

## Tech Highlights

| Layer | What It Does |
|---|---|
| Audio Capture | Persistent background audio stream, tuned for low-latency hotkey response |
| Chunking & Segmentation | Long speech is split into overlap-merged segments to avoid cutoffs mid-sentence |
| Transcription Engine | Speech-to-text decoding tuned through iterative trial-and-error, not default settings |
| AI Enhancement | Multi-provider LLM layer with dynamic output-length safety checks |
| Licensing | Multi-layer hardware-bound validation system |

*(Full engineering breakdown in [docs/ENGINEERING.md](docs/ENGINEERING.md) — implementation-level detail intentionally withheld; see [License & Usage](#license--usage).)*

## Reliability Philosophy

Speech is messy — pauses, background noise, half-finished sentences. Typly treats a wrong or hallucinated transcription as a worse outcome than a slightly delayed one, so its decoding pipeline includes dedicated safeguards against cut-off and fabricated text rather than optimizing purely for speed. The same philosophy carries into AI enhancement: if the enhancement step fails or times out, the user still gets their raw, accurate transcription — a broken AI call never means a broken result.

## Pricing

| Plan | Duration | Price |
|---|---|---|
| Trial | 7 days | Free |
| 1 Month | 30 days | $6 |
| 3 Month | 90 days | $15 |
| 6 Month | 180 days | $35 |
| Enterprise | 365 days (API access included) | $80 |

> Payment accepted via crypto (BTC, ETH, BNB, XRP, TRX, LTC) and other methods. Message us on Facebook / WhatsApp / Email with your Machine ID (visible inside **Settings**) to receive payment instructions.

## Download

**[⬇ Download Typly for Windows](https://github.com/muhammadantor/typly-bangla-voice-typing/releases/tag/v1.0.0)**

> ⚠️ Typly is an independently-distributed build. Windows SmartScreen or your antivirus may show a warning on first launch — this is expected for independently-distributed software, not a sign of malware. Click **"More info" → "Run anyway"** to proceed.

## System Requirements

| Requirement | Minimum |
|---|---|
| OS | Windows 10 / 11 (64-bit) |
| CPU | Intel i3 6th Gen or equivalent |
| RAM | 8 GB |
| Internet | Required on first launch only (~250MB model download) |
| GPU | Optional — NVIDIA GPU for acceleration (CPU works fine without it) |

## Good to Know (Not Bugs)

- **Administrator permission is required every launch** — Typly needs elevated rights to register its global hotkey system-wide. This is a Windows security requirement, not a malfunction.
- **The "Launch app now" checkbox after install may not open Typly** — due to the same permission requirement. Please open Typly manually from the Desktop shortcut after installation.
- **Auto-start with Windows may not always trigger reliably** — for the same reason. A workaround is covered in the installation guide.
- **GPU acceleration is NVIDIA-only** — AMD/Intel GPU users run in CPU mode automatically. Fully functional, just not GPU-accelerated.

## Documentation

| Doc | Covers |
|---|---|
| [docs/ENGINEERING.md](docs/ENGINEERING.md) | Full engine pipeline — audio capture, chunking, transcription, AI enhancement |
| [docs/SECURITY.md](docs/SECURITY.md) | License & security architecture |
| [docs/INSTALLATION.md](docs/INSTALLATION.md) | Step-by-step install & setup guide |
| [docs/COMPARISON.md](docs/COMPARISON.md) | Typly vs. traditional voice-typing tools, in more depth |
| [docs/FAQ.md](docs/FAQ.md) | Troubleshooting & common questions |

## FAQ

**Is Typly open source?** No. This repository is for distribution and documentation only — see [License & Usage](#license--usage).

**Why does Windows show a security warning when I install it?** Because Typly is independently distributed, not because it's unsafe. See the note under [Download](#download).

**Does it work without an internet connection?** Yes, after the first launch (which downloads the language model, ~250MB). Day-to-day use is fully offline.

**Do I need a powerful GPU?** No — a GPU speeds things up if it's NVIDIA, but Typly runs entirely on CPU as well.

## 👤 About The Builder

<div align="center">

<img src="developer-photo.png" width="140" style="border-radius:50%;" alt="Muhammad Antor">

**Muhammad Antor**
AI Automation Engineer | AutomateIQ Labs 🇧🇩

*"I don't just write code — I build systems that work while you sleep."*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/muhammad-antor)
[![Facebook](https://img.shields.io/badge/AutomateIQ_Labs-Follow-1877F2?style=for-the-badge&logo=facebook)](https://www.facebook.com/automateiq.labs/)
[![Email](https://img.shields.io/badge/Email-Hire_Me-EA4335?style=for-the-badge&logo=gmail)](mailto:muhammadantor71@gmail.com)

</div>

## License & Usage

Typly is proprietary, closed-source software. This repository exists to demonstrate the product, its engineering, and its security model — not to serve as a rebuild guide.

❌ **Not Permitted:** reverse engineering, decompiling, redistribution, or license circumvention.

If you're interested in a similar system built for your business, reach out below.

## Connect

<div align="center">

**Muhammad Antor** — AI Automation Engineer & Founder, AutomateIQ Labs 🇧🇩

[![Facebook](https://img.shields.io/badge/AutomateIQ_Labs-Follow-1877F2?style=for-the-badge&logo=facebook)](https://www.facebook.com/automateiq.labs/)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-Message-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/8801959884930)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/muhammadantor)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail)](mailto:muhammadantor71@gmail.com)
[![Instagram](https://img.shields.io/badge/Instagram-Follow-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/automateiq.labs/)

</div>

---

<div align="center">

*Distribution repository by AutomateIQ Labs — the underlying implementation is proprietary and not licensed for reuse.*

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%"/>

</div>
