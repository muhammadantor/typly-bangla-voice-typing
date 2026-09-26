# Installation Guide

[← Back to README](../README.md)

---

## Table of Contents

- [Before You Start](#before-you-start)
- [Step-by-Step Installation](#step-by-step-installation)
- [First Launch](#first-launch)
- [Why Administrator Permission Is Required](#why-administrator-permission-is-required)
- [Setting Up Reliable Auto-Start](#setting-up-reliable-auto-start)
- [Activating Your License](#activating-your-license)
- [Uninstalling](#uninstalling)

---

## Before You Start

Check that your system meets the minimum requirements in the [README](../README.md#system-requirements) — Windows 10/11 (64-bit), at least 8GB RAM, and an internet connection for first launch only.

## Step-by-Step Installation

1. **Download** the installer from the [Releases page](../README.md#download).
2. **Run the installer.** Windows SmartScreen may show a warning since Typly is an independently-distributed build — this is expected. Click **"More info" → "Run anyway"** to proceed.
3. **Follow the setup wizard.** Choose your install location and confirm.
4. **Do not rely on the "Launch app now" checkbox at the end of setup** — see [Why Administrator Permission Is Required](#why-administrator-permission-is-required) below for why, and how to open Typly correctly.
5. **Open Typly manually** from the Desktop shortcut or Start Menu after installation completes.

## First Launch

On first launch, Typly downloads its speech-recognition model (~250MB) — this requires an active internet connection and may take a few minutes depending on your connection speed. After this one-time download, Typly works fully offline for day-to-day use.

## Why Administrator Permission Is Required

Typly needs to register a **global system-wide hotkey** (Win + Ctrl) so it can activate from inside any application, not just its own window. Windows requires elevated (Administrator) permission to register a hook of this kind at the system level — this is a Windows security boundary, not a Typly design choice.

This has two practical effects you should expect, not treat as bugs:

- **A User Account Control (UAC) prompt appears every time you launch Typly.** This is normal — click "Yes" to allow it.
- **The installer's "Launch app now" checkbox often does not open Typly.** The installer itself doesn't run with elevated rights by default, so the handoff to launch Typly can silently fail. Always open Typly manually after installing.

## Setting Up Reliable Auto-Start

Because Typly requires Administrator rights, Windows' built-in "Start with Windows" toggle (inside Typly's Settings tab) may not reliably launch it on every boot — the same elevation requirement applies at startup as it does to manual launches.

For a more reliable auto-start, set up a Task Scheduler entry that launches Typly with elevated rights at login:

1. Open **Task Scheduler** (search for it in the Start Menu).
2. Click **Create Task** (not "Create Basic Task").
3. Under the **General** tab: name it "Typly Auto-Start", and check **"Run with highest privileges."**
4. Under the **Triggers** tab: click **New**, set it to **"At log on."**
5. Under the **Actions** tab: click **New**, set Action to **"Start a program,"** and browse to Typly's installed `.exe` path.
6. Save the task. Typly will now launch with the correct permissions automatically at every login.

## Activating Your License

1. Open Typly and go to the **License** tab.
2. Find your **Machine ID** displayed there.
3. Send your Machine ID to us via [Facebook, WhatsApp, or Email](../README.md#connect) along with your preferred plan (see [Pricing](../README.md#pricing)).
4. Once payment is confirmed, you'll receive an activation code — enter it in the **License** tab and click **Activate**.

## Uninstalling

Use Windows' standard **Settings → Apps → Installed Apps**, find Typly, and click Uninstall. This removes the application; your license remains tied to your hardware, so reinstalling and reactivating on the same machine does not require a new purchase.

---

[← Back to README](../README.md) · [← Security Architecture](SECURITY.md) · [Comparison →](COMPARISON.md)
