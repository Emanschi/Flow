<!--
  Flow - A high-performance teleprompter for Windows.
  Copyright (C) 2026 Waled Alturkmani (LumoRez07)

  This program is free software: you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation, either version 3 of the License, or
  (at your option) any later version.
-->

<div align="center">

<p align="center">
  <img src="src/assets/readme-assets/github-readme-header.webp" width="960" alt="Flow Teleprompter v2" />
</p>

<table align="center">
  <tr>
    <td align="center"><img src="src/assets/readme-assets/en-circle-active.webp" width="32" height="32" alt="English" /><br /><sub><b>English</b></sub></td>
    <td align="center"><a href="README.es.md"><img src="src/assets/readme-assets/es-circle.webp" width="32" height="32" alt="Español" /><br /><sub><b>Español</b></sub></a></td>
    <td align="center"><a href="README.tr.md"><img src="src/assets/readme-assets/tr-circle.webp" width="32" height="32" alt="Türkçe" /><br /><sub><b>Türkçe</b></sub></a></td>
    <td align="center"><a href="README.ar.md"><img src="src/assets/readme-assets/sa-circle.webp" width="32" height="32" alt="العربية" /><br /><sub><b>العربية</b></sub></a></td>
    <td align="center"><a href="README.de.md"><img src="src/assets/readme-assets/de-circle.webp" width="32" height="32" alt="Deutsch" /><br /><sub><b>Deutsch</b></sub></a></td>
    <td align="center"><a href="README.fr.md"><img src="src/assets/readme-assets/fr-circle.webp" width="32" height="32" alt="Français" /><br /><sub><b>Français</b></sub></a></td>
    <td align="center"><a href="README.pt.md"><img src="src/assets/readme-assets/br-circle.webp" width="32" height="32" alt="Português" /><br /><sub><b>Português</b></sub></a></td>
    <td align="center"><a href="README.fi.md"><img src="src/assets/readme-assets/fi-circle.webp" width="32" height="32" alt="Suomi" /><br /><sub><b>Suomi</b></sub></a></td>
  </tr>
</table>

<p align="center">
  <a href="https://github.com/LumoRez07/Flow">
    <img src="https://img.shields.io/badge/fork%20of-LumoRez07%2FFlow-24292f?style=flat-square&logo=github&logoColor=white" alt="Fork of LumoRez07/Flow" />
  </a>
  <img src="https://img.shields.io/badge/platform-Linux%20(unofficial)-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux (unofficial fork)" />
  <img src="https://img.shields.io/badge/backend-Rust%20%2B%20Tauri%20v2-FFC131?style=flat-square&logo=tauri&logoColor=black" alt="Tauri + Rust" />
  <img src="https://img.shields.io/badge/license-GPLv3-22c55e?style=flat-square" alt="GPLv3 License" />
</p>

</div>

---

> ### 🐧 This is an unofficial, community-maintained Linux fork
>
> **Flow** is a Windows teleprompter app created by [LumoRez07](https://github.com/LumoRez07). This repository is a **fork** that adds a native Linux build (AppImage, `.deb`, `.rpm`, Arch `PKGBUILD`) on top of the same codebase — it is **not** the official project, and it is **not** distributed through the Microsoft Store, SourceForge, or upstream GitHub Releases.
>
> The Linux support was offered upstream as a [pull request](https://github.com/LumoRez07/Flow/pull/3); the maintainer [declined to merge it](https://github.com/LumoRez07/Flow/pull/3#issuecomment-5464963891) since Linux isn't on their roadmap and they can't test/maintain it themselves, but explicitly said this fork is welcome to keep existing under the GPL license. That means:
>
> - **For the original Windows app** — full feature list, screenshots, official downloads, and the project roadmap — see **[github.com/LumoRez07/Flow](https://github.com/LumoRez07/Flow)**. This document only covers what's specific to the Linux build.
> - **This fork can lag behind upstream.** New Windows-side features/fixes land here only whenever someone manually pulls them in; there's no guarantee of staying in sync.
> - Bugs specific to the Linux packaging belong in **this repository's** issue tracker, not upstream's.

---

## What's different on Linux

Everything not listed here (playback styles, script editor, voice tracking, remote messaging, realtime editing, AI-assisted rewriting, the Windows overlay/updater, etc.) works the same as described in the [upstream README](https://github.com/LumoRez07/Flow) — this fork doesn't change any of that, it only adds Linux packaging and a handful of Linux-specific adaptations.

Honest limitations compared to Windows:

| Feature | Linux |
| --- | --- |
| Screen-capture protection | Not available — the underlying API is Windows-only, with no X11/Wayland equivalent. |
| Wayland | Runs via XWayland by default (always-on-top, absolute positioning, and global hotkeys need it); native Wayland is opt-in but breaks those three. |
| Remote Control | Works, but needs a one-time manual firewall exception for TCP port 43127 (most Linux desktops default-deny inbound connections, unlike Windows' first-launch prompt). |
| In-app auto-update | Works for the AppImage; `.deb`/`.rpm`/`PKGBUILD` installs update through your distro's package manager instead. |
| Distribution | No pre-built binaries published yet — see [Getting started](#getting-started) below. |

## Getting started

There are no official pre-built Linux binaries yet. Options, easiest first:

1. **Arch Linux**: use the provided [`PKGBUILD`](packaging/arch/PKGBUILD) (builds from source) or [`PKGBUILD-bin`](packaging/arch/PKGBUILD-bin) (once a release with binary assets exists).
2. **Any distro**: grab an AppImage/`.deb`/`.rpm` artifact from the [Linux CI workflow](.github/workflows/build-linux.yml)'s latest successful run.
3. **Build from source**: see [BUILDING-LINUX.md](BUILDING-LINUX.md) for per-distro prerequisites and build commands.

For Windows, use the official channels linked in the [upstream README](https://github.com/LumoRez07/Flow) (Microsoft Store, GitHub Releases, SourceForge).

## Development

This fork's changes are Linux-only (no `#[cfg(windows)]` code or shared Tauri config was touched). For Linux prerequisites, build commands, and known build-time issues, see **[BUILDING-LINUX.md](BUILDING-LINUX.md)**.

For Windows development, see the [upstream repository](https://github.com/LumoRez07/Flow).

---

## Privacy

Same data-handling behavior as upstream — most data stays local, voice tracking runs locally via Vosk, and Groq requests are only sent when AI features are used. See [privacy-policy.md](privacy-policy.md).

---

## License

Like upstream, this project is licensed under GPL-3.0-or-later. See [LICENSE](LICENSE). All original authorship remains with [LumoRez07](https://github.com/LumoRez07); this repository's Linux-specific changes are additions on top of that codebase, also released under GPLv3.

---

## Star History

<a href="https://www.star-history.com/?repos=Emanschi%2FFlow&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&legend=top-left" />
 </picture>
</a>
