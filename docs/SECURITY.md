# Security & Licensing Architecture

[← Back to README](../README.md)

> This document explains what Typly's licensing system protects and why — not how it's implemented. Exact algorithms, storage locations, and validation code are intentionally withheld; see [License & Usage](../README.md#license--usage).

---

## Table of Contents

- [Why Licensing Is Treated as a Core Engineering Problem](#why-licensing-is-treated-as-a-core-engineering-problem)
- [The 7-Layer Validation System](#the-7-layer-validation-system)
- [Threat Model & Honest Limitations](#threat-model--honest-limitations)
- [FAQ](#faq)

---

## Why Licensing Is Treated as a Core Engineering Problem

Most small independent software gets its licensing bolted on as an afterthought — a single key check that's trivial to bypass once found. Typly's licensing was designed alongside the core engine, not after it, because a payment-supported product's business model is only as strong as its weakest license check.

## The 7-Layer Validation System

| Layer | Purpose |
|---|---|
| **1. Hardware Fingerprinting** | Ties a license to the specific machine it was activated on, using a combination of stable hardware identifiers — deliberately excluding network MAC address, since MAC values can be trivially spoofed in software and would make the fingerprint unreliable rather than more secure. |
| **2. AES-256-GCM Encryption** | The license payload is encrypted at rest, so it can't be read or edited by opening the file in a text editor. |
| **3. HMAC Integrity Verification** | Detects whether a license file has been modified since it was issued — even a single-byte change invalidates it. |
| **4. Obfuscated Persistence** | License data is not stored in an obvious, easily-discoverable location. |
| **5. Filesystem/Registry Access Control** | The license store is protected against casual deletion, making a simple "delete and reset" bypass significantly harder. |
| **6. Time-Consistency Validation** | Checks for inconsistencies that would indicate system clock manipulation, a common method for extending trial periods or expired licenses. |
| **7. Startup Integrity Self-Check** | Typly verifies its own license-validation logic hasn't been patched or replaced before trusting the result of any check above. |

Each layer is independent — defeating one does not automatically defeat the others, which is the core design goal of a layered system over a single check.

## Threat Model & Honest Limitations

No client-side license system is unbreakable — this is true of every desktop software license on the market, not a weakness unique to Typly. A sufficiently determined attacker with full system access and reverse-engineering expertise can, in principle, defeat any local validation system.

What this architecture is designed to do is **raise the cost and skill required to bypass licensing far above casual tampering** — deleting a file, editing a registry value, or changing the system clock will not work. That is a realistic and honest goal, and it's the same goal every serious commercial software vendor works toward.

## FAQ

**Can I move my license to a new PC?** Contact support with your old and new Machine ID — licenses are hardware-bound by design, but transfers are handled manually on request.

**What happens if I reinstall Windows?** Your hardware fingerprint typically stays the same after a reinstall (same physical components), so reactivation should work normally. Contact support if it doesn't.

**Is this system unbreakable?** No — see [Threat Model & Honest Limitations](#threat-model--honest-limitations) above. It's engineered to resist casual tampering, not to claim an impossible guarantee.

**Why exclude the MAC address from the hardware fingerprint?** Because MAC addresses can be changed in software on most systems, including one via a simple driver setting — using it would make the fingerprint easier to spoof, not harder.

---

[← Back to README](../README.md) · [← Engineering Deep-Dive](ENGINEERING.md) · [Installation Guide →](INSTALLATION.md)
