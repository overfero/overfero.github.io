---
title: "Optical Transfer"
excerpt: "Move files between devices with nothing but a camera and a screen: animated QR codes, RaptorQ fountain coding, no network.<br/><img src='/images/500x300.png' width='300' height='200'>"
collection: portfolio
permalink: /optical-transfer/
---

# Optical Transfer

Move photos, files, or text between devices with nothing between them but a camera and a screen. No network, no pairing, no account. The sender plays the payload as an endless stream of animated QR codes; the receiving device points its camera at it and rebuilds the file.

**Try it in a browser:** [kriscris.github.io/optical-transfer](https://kriscris.github.io/optical-transfer/). Open it on both devices, choose *Send* on one and *Receive* on the other. It installs to the home screen and then works with no network at all. Native desktop apps for Windows, macOS and Linux (x86-64 and arm64) are built by CI on every push.

It speaks its own wire format, v4: RaptorQ fountain coding behind a 16-byte frame header, files up to 128 MiB, and optional colour codes that carry three QR codes in one. Every receiver also reads wire v3, the format of [Decimen Optical Transfer](https://github.com/bashalarmistalt/decimen-optical-transfer).

## Features:
- **No Network Required**: Transfer happens entirely through a camera reading a screen — no Wi-Fi, Bluetooth, pairing, or account needed.
- **RaptorQ Fountain Coding**: Wire format v4 uses RaptorQ fountain coding behind a 16-byte frame header, supporting files up to 128 MiB.
- **Colour QR Codes**: An optional mode packs three QR codes into the red, green, and blue channels of a single code for higher throughput.
- **Backward Compatible**: Every receiver can also read wire v3, interoperating with Decimen Optical Transfer.
- **Cross-Platform**: Works as an offline-installable PWA in the browser, plus native desktop apps for Windows, macOS, and Linux on x86-64 and arm64.
- **Double-Verified Integrity**: Nothing is shown to the user until two independent checks agree — the frame header's FNV-1a over the assembled container, and the container's own SHA-256 over the file inside it.
- **Speed Presets**: Five presets (Reliable, Balanced, Fast, Colour, Max) trade code density and frame rate for throughput, up to roughly 344 KiB/s on the wire.
- **Stateless Wire Protocol**: No handshake, no back channel — a receiver can lock onto a stream mid-transfer and rebuild the file from wherever it started.

## Repository:
- [GitHub Repository](https://github.com/KrisCris/optical-transfer)

## Live Demo:
- [kriscris.github.io/optical-transfer](https://kriscris.github.io/optical-transfer/)
