# Troubleshooting & FAQ

[← Back to README](../README.md)

---

## Table of Contents

- [Installation & Launch Issues](#installation--launch-issues)
- [Hotkey & Usage Issues](#hotkey--usage-issues)
- [Performance & Hardware](#performance--hardware)
- [Licensing & Payment](#licensing--payment)
- [General Questions](#general-questions)

---

## Installation & Launch Issues

**Windows shows a security warning ("Windows protected your PC") when I run the installer.**
This appears because Typly is an independently-distributed build, not because it's unsafe. Click **"More info" → "Run anyway"** to proceed. See [Download](../README.md#download) for details.

**I checked "Launch app now" at the end of setup, but nothing opened.**
This is expected — see [Why Administrator Permission Is Required](INSTALLATION.md#why-administrator-permission-is-required). Open Typly manually from the Desktop shortcut instead.

**A permission prompt (UAC) appears every time I open Typly.**
Normal behavior — click "Yes." Typly needs elevated rights to register its system-wide hotkey. This happens on every launch, not just the first.

**Typly doesn't start automatically when I turn on my PC, even though I enabled "Start with Windows."**
Because of the same permission requirement above, the built-in toggle isn't fully reliable. Set up a Task Scheduler entry instead — full steps in [Setting Up Reliable Auto-Start](INSTALLATION.md#setting-up-reliable-auto-start).

## Hotkey & Usage Issues

**The hotkey doesn't respond when I hold Win + Ctrl.**
Confirm Typly is running (check the system tray icon). If it's running but still unresponsive, close and reopen it — some other applications also use global hotkey hooks and can occasionally conflict.

**My speech gets cut off mid-sentence in longer dictations.**
Typly processes speech in chunks with overlap-merging specifically to avoid this (see [Engineering Deep-Dive](ENGINEERING.md#2-chunking--segmentation)). If you still notice cutoffs, check your microphone isn't losing signal (loose cable, Bluetooth dropout) partway through.

**Mixed Bangla-English speech isn't transcribing correctly.**
Make sure **Mixed mode** is selected in the Main tab rather than a single-language mode — single-language modes are optimized for one language and may misinterpret code-switched speech.

## Performance & Hardware

**Is Typly slower on my PC than advertised?**
Transcription speed depends heavily on whether GPU acceleration is active. Typly only accelerates on **NVIDIA** GPUs — AMD/Intel GPU systems run in CPU mode automatically, which is fully functional but slower. See [Hardware Usage](COMPARISON.md#hardware-usage).

**Can I force GPU mode on a non-NVIDIA system?**
No — GPU acceleration depends on NVIDIA-specific compute libraries. This is a hardware/ecosystem limitation, not a setting that can be toggled.

## Licensing & Payment

**How do I purchase a license?**
Open the **License** tab, copy your Machine ID, and message it to us via [Facebook, WhatsApp, or Email](../README.md#connect) with your preferred plan. See [Activating Your License](INSTALLATION.md#activating-your-license).

**I reinstalled Windows — do I need to buy a new license?**
Usually not — your hardware fingerprint typically stays the same after an OS reinstall. Reactivate with your existing Machine ID; contact support if it doesn't work.

**Can I use my license on two computers?**
Licenses are hardware-bound to a single machine by design. Contact support if you need to transfer a license to a new device.

**Is my license truly impossible to bypass?**
No system is unbreakable — see the honest [Threat Model & Limitations](SECURITY.md#threat-model--honest-limitations) note. It's engineered to resist casual tampering, which is the realistic goal of any commercial licensing system.

## General Questions

**Does Typly work without an internet connection?**
Yes, after the one-time model download on first launch. Day-to-day dictation is fully offline. AI enhancement (optional) needs internet only if you're using a cloud-based LLM provider.

**Is Typly open source?**
No. This repository exists for distribution and documentation only — see [License & Usage](../README.md#license--usage).

**Can I request a similar tool built for my own business or use case?**
Yes — reach out via [Connect](../README.md#connect).

---

[← Back to README](../README.md) · [← Comparison](COMPARISON.md)
