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
    <td align="center"><a href="README.md"><img src="src/assets/readme-assets/en-circle.webp" width="32" height="32" alt="English" /><br /><sub><b>English</b></sub></a></td>
    <td align="center"><a href="README.es.md"><img src="src/assets/readme-assets/es-circle.webp" width="32" height="32" alt="Español" /><br /><sub><b>Español</b></sub></a></td>
    <td align="center"><a href="README.tr.md"><img src="src/assets/readme-assets/tr-circle.webp" width="32" height="32" alt="Türkçe" /><br /><sub><b>Türkçe</b></sub></a></td>
    <td align="center"><a href="README.ar.md"><img src="src/assets/readme-assets/sa-circle.webp" width="32" height="32" alt="العربية" /><br /><sub><b>العربية</b></sub></a></td>
    <td align="center"><img src="src/assets/readme-assets/de-circle-active.webp" width="32" height="32" alt="Deutsch" /><br /><sub><b>Deutsch</b></sub></td>
    <td align="center"><a href="README.fr.md"><img src="src/assets/readme-assets/fr-circle.webp" width="32" height="32" alt="Français" /><br /><sub><b>Français</b></sub></a></td>
    <td align="center"><a href="README.pt.md"><img src="src/assets/readme-assets/br-circle.webp" width="32" height="32" alt="Português" /><br /><sub><b>Português</b></sub></a></td>
    <td align="center"><a href="README.fi.md"><img src="src/assets/readme-assets/fi-circle.webp" width="32" height="32" alt="Suomi" /><br /><sub><b>Suomi</b></sub></a></td>
  </tr>
</table>

<p align="center">
  <a href="https://github.com/LumoRez07/Flow">
    <img src="https://img.shields.io/badge/Fork%20von-LumoRez07%2FFlow-24292f?style=flat-square&logo=github&logoColor=white" alt="Fork von LumoRez07/Flow" />
  </a>
  <img src="https://img.shields.io/badge/Plattform-Linux%20(inoffiziell)-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux (inoffizieller Fork)" />
  <img src="https://img.shields.io/badge/Backend-Rust%20%2B%20Tauri%20v2-FFC131?style=flat-square&logo=tauri&logoColor=black" alt="Tauri + Rust" />
  <img src="https://img.shields.io/badge/Lizenz-GPLv3-22c55e?style=flat-square" alt="GPLv3-Lizenz" />
</p>

</div>

---

> ### 🐧 Dies ist ein inoffizieller, von der Community gepflegter Linux-Fork
>
> **Flow** ist eine Windows-Teleprompter-App von [LumoRez07](https://github.com/LumoRez07). Dieses Repository ist ein **Fork**, der auf demselben Codebasis einen nativen Linux-Build ergänzt (AppImage, `.deb`, `.rpm`, Arch-`PKGBUILD`) — es ist **nicht** das offizielle Projekt und wird **nicht** über den Microsoft Store, SourceForge oder die GitHub Releases des Originals vertrieben.
>
> Die Linux-Unterstützung wurde dem Original-Projekt als [Pull Request](https://github.com/LumoRez07/Flow/pull/3) angeboten; der Maintainer hat [das Mergen abgelehnt](https://github.com/LumoRez07/Flow/pull/3#issuecomment-5464963891), da Linux nicht auf seiner Roadmap steht und er es selbst nicht testen/pflegen kann — er hat aber ausdrücklich gesagt, dass dieser Fork unter der GPL-Lizenz gerne bestehen bleiben darf. Das bedeutet konkret:
>
> - **Für die originale Windows-App** — vollständige Funktionsliste, Screenshots, offizielle Downloads und die Projekt-Roadmap — siehe **[github.com/LumoRez07/Flow](https://github.com/LumoRez07/Flow)**. Dieses Dokument beschreibt nur, was am Linux-Build anders ist.
> - **Dieser Fork kann hinter dem Original zurückliegen.** Neue Funktionen/Fixes von der Windows-Seite landen hier nur, wenn sie jemand manuell nachzieht — es gibt keine Garantie für einen synchronen Stand.
> - Fehler, die speziell die Linux-Paketierung betreffen, gehören in den Issue-Tracker **dieses Repositories**, nicht in den des Originals.

---

## Was auf Linux anders ist

Alles, was hier nicht aufgeführt ist (Wiedergabe-Stile, Skript-Editor, Sprachverfolgung, Fernnachrichten, Realtime-Editing, KI-gestütztes Umschreiben, das Windows-Overlay/der Updater usw.), funktioniert genauso wie im [README des Originals](https://github.com/LumoRez07/Flow) beschrieben — dieser Fork ändert daran nichts, sondern ergänzt nur die Linux-Paketierung und ein paar Linux-spezifische Anpassungen.

Ehrliche Übersicht der Einschränkungen gegenüber Windows:

| Funktion | Linux |
| --- | --- |
| Schutz vor Bildschirmaufnahme | Nicht verfügbar — die zugrunde liegende API ist Windows-exklusiv, ein Äquivalent für X11/Wayland gibt es nicht. |
| Wayland | Läuft standardmäßig über XWayland (Always-on-Top, absolute Fensterpositionierung und globale Hotkeys benötigen es); natives Wayland ist optional aktivierbar, bricht dabei aber genau diese drei Funktionen. |
| Fernsteuerung (Remote Control) | Funktioniert, benötigt aber einmalig eine manuelle Firewall-Freigabe für TCP-Port 43127 (die meisten Linux-Desktops blockieren eingehende Verbindungen standardmäßig, anders als der Erstlaunch-Dialog unter Windows). |
| Automatisches In-App-Update | Funktioniert bei der AppImage; `.deb`/`.rpm`/`PKGBUILD`-Installationen werden stattdessen über den Paketmanager der Distribution aktualisiert. |
| Distribution | Es gibt noch keine fertig gebauten Releases — siehe [Erste Schritte](#erste-schritte) unten. |

## Erste Schritte

Es gibt noch keine offiziellen, fertig gebauten Linux-Binärdateien. Optionen, einfachste zuerst:

1. **Arch Linux**: das mitgelieferte [`PKGBUILD`](packaging/arch/PKGBUILD) (baut aus dem Quellcode) oder [`PKGBUILD-bin`](packaging/arch/PKGBUILD-bin) (sobald ein Release mit Binär-Assets existiert) verwenden.
2. **Beliebige Distribution**: ein AppImage-/`.deb`-/`.rpm`-Artefakt aus dem letzten erfolgreichen Lauf des [Linux-CI-Workflows](.github/workflows/build-linux.yml) holen.
3. **Selbst aus dem Quellcode bauen**: siehe [BUILDING-LINUX.md](BUILDING-LINUX.md) für Voraussetzungen je Distribution und Build-Befehle.

Für Windows die offiziellen Kanäle nutzen, die im [README des Originals](https://github.com/LumoRez07/Flow) verlinkt sind (Microsoft Store, GitHub Releases, SourceForge).

## Entwicklung

Die Änderungen dieses Forks betreffen ausschließlich Linux (kein `#[cfg(windows)]`-Code oder gemeinsam genutzte Tauri-Konfiguration wurde angefasst). Voraussetzungen, Build-Befehle und bekannte Probleme beim Bauen stehen in **[BUILDING-LINUX.md](BUILDING-LINUX.md)**.

Für die Windows-Entwicklung siehe das [Original-Repository](https://github.com/LumoRez07/Flow).

---

## Datenschutz

Gleiches Datenverhalten wie im Original — die meisten Daten bleiben lokal, Sprachverfolgung läuft lokal über Vosk-Modelle, und Groq-Anfragen werden nur gesendet, wenn KI-Funktionen genutzt werden. Siehe [privacy-policy.md](privacy-policy.md).

---

## Lizenz

Wie das Original steht auch dieses Projekt unter GPL-3.0-or-later. Siehe [LICENSE](LICENSE). Die ursprüngliche Urheberschaft bleibt vollständig bei [LumoRez07](https://github.com/LumoRez07); die Linux-spezifischen Ergänzungen dieses Repositories sind Erweiterungen auf dieser Codebasis, ebenfalls unter GPLv3 veröffentlicht.

---

## Star-Verlauf (Star History)

<a href="https://www.star-history.com/?repos=Emanschi%2FFlow&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=Emanschi/Flow&type=date&legend=top-left" />
 </picture>
</a>
