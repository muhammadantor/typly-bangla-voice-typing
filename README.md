<p align="center">
  <img src="typly-icon.png" width="120" alt="Typly Icon">
</p>

<h1 align="center">Typly — AI-Powered Bangla & English Voice Typing for Windows</h1>

**A background voice-typing assistant for Windows — hold a hotkey, speak in Bangla or English, and your words appear instantly wherever your cursor is. Built by AutomateIQ Labs.**

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white">
  <img src="https://img.shields.io/badge/Languages-Bangla%20%2B%20English-2E8B57?style=for-the-badge">
  <img src="https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge">
  <img src="https://img.shields.io/badge/Maintained%20by-AutomateIQ%20Labs-black?style=for-the-badge">
</p>

> 📌 **This repository is for distribution and documentation only.** It showcases the product, its engineering, and its security model. No source code is published here — see [License & Usage](#license--usage) below.

**Core keywords:** AI voice typing Windows, Bangla speech-to-text, English voice dictation, hands-free typing tool, voice-to-text software, AI transcription app, Windows dictation assistant, Bangla voice recognition, speech AI Bangladesh, offline voice typing tool.

---

## Table of Contents

- [Overview](#overview)
- [The Problem It Solves](#the-problem-it-solves)
- [Screenshots](#screenshots)
- [What Makes Typly Different](#what-makes-typly-different)
- [Tech Highlights](#tech-highlights)
- [Pricing](#pricing)
- [Download](#download)
- [System Requirements](#system-requirements)
- [Good to Know (Not Bugs)](#good-to-know-not-bugs)
- [Documentation](#documentation)
- [FAQ](#faq)
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

## What Makes Typly Different

- 🎯 **True system-wide hotkey** — works inside any app, no window focus required
- 🇧🇩🇬🇧 **Real dual-language support** — Bangla, English, and Mixed mode, not just English with poor Bangla accuracy
- 🧠 **Optional AI enhancement layer** — raw transcription can be polished for grammar and tone via 9+ LLM providers (bring your own API key)
- ⚡ **Automatic GPU detection** — uses NVIDIA GPU acceleration when available, falls back cleanly to CPU
- 🔒 **Hardware-locked licensing** — tied to the machine, engineered to resist casual tampering
- 📊 **Live usage visibility** — daily and weekly word usage tracked inside the app, not hidden

## Tech Highlights

| Layer | What It Does |
|---|---|
| Audio Capture | Persistent background audio stream, tuned for low-latency hotkey response |
| Chunking & Segmentation | Long speech is split into overlap-merged segments to avoid cutoffs mid-sentence |
| Transcription Engine | Speech-to-text decoding tuned through iterative trial-and-error, not default settings |
| AI Enhancement | Multi-provider LLM layer with dynamic output-length safety checks |
| Licensing | Multi-layer hardware-bound validation system |

*(Full engineering breakdown in [docs/ENGINEERING.md](docs/ENGINEERING.md) — implementation-level detail intentionally withheld; see [License & Usage](#license--usage).)*

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
| `docs/ENGINEERING.md` | Full engine pipeline — audio capture, chunking, transcription, AI enhancement |
| `docs/SECURITY.md` | License & security architecture |
| `docs/INSTALLATION.md` | Step-by-step install & setup guide |
| `docs/COMPARISON.md` | Typly vs. traditional voice-typing tools |
| `docs/FAQ.md` | Troubleshooting & common questions |

## FAQ

**Is Typly open source?** No. This repository is for distribution and documentation only — see [License & Usage](#license--usage).

**Why does Windows show a security warning when I install it?** Because Typly is independently distributed, not because it's unsafe. See the note under [Download](#download).

**Does it work without an internet connection?** Yes, after the first launch (which downloads the language model, ~250MB). Day-to-day use is fully offline.

**Do I need a powerful GPU?** No — a GPU speeds things up if it's NVIDIA, but Typly runs entirely on CPU as well.

## License & Usage

Typly is proprietary, closed-source software. This repository exists to demonstrate the product, its engineering, and its security model — not to serve as a rebuild guide.

❌ **Not Permitted:** reverse engineering, decompiling, redistribution, or license circumvention.

If you're interested in a similar system built for your business, reach out below.

## Connect

**Muhammad Antor** — AI Automation Engineer & Founder, AutomateIQ Labs 🇧🇩

- Facebook: [facebook.com/automateiq.labs](https://facebook.com/automateiq.labs)
- WhatsApp: +880 1959-884930
- Email: muhammadantor71@gmail.com
- Instagram: [instagram.com/automateiq.labs](https://instagram.com/automateiq.labs)

---

<p align="center"><sub>Distribution repository by <b>AutomateIQ Labs</b> — the underlying implementation is proprietary and not licensed for reuse.</sub></p>
