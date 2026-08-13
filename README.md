![MiPow Integration für Home Assistant](https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/assets/mipow-banner.svg)

# MiPow

**Bluetooth-LED-Kerzen (Playbulb) in Home Assistant steuern.**

[![Release](https://img.shields.io/github/v/release/dhaucke/hassio-mipow?style=flat-square)](https://github.com/dhaucke/hassio-mipow/releases/latest)
[![HACS](https://img.shields.io/badge/HACS-Custom-41BDF5?style=flat-square)](https://github.com/hacs/integration)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Custom%20Integration-18BCF2?style=flat-square)](https://www.home-assistant.io/)
[![License](https://img.shields.io/github/license/dhaucke/hassio-mipow?style=flat-square)](LICENSE)

**Farbe · Weißlicht · Effekte · Timer · Batteriestand**

[Mit HACS installieren](https://my.home-assistant.io/redirect/hacs_repository/?owner=dhaucke&repository=hassio-mipow&category=integration) · [Problem melden](https://github.com/dhaucke/hassio-mipow/issues)

**Sprache:** [Deutsch](#deutsch) · [English](#english)

---

# Deutsch

## Warum dieser Fork existiert

Dies ist ein Fork von [D3M80L/hassio-mipow](https://github.com/D3M80L/hassio-mipow). Der letzte Commit des Original-Maintainers liegt schon länger zurück, seitdem ist die Integration auf aktuellem Home Assistant komplett kaputt: `ModuleNotFoundError: No module named 'homeassistant.backports.enum'` (siehe [Issue #18](https://github.com/D3M80L/hassio-mipow/issues/18)) — HA hat dieses Backport-Modul entfernt. Ein passender Fix lag als [PR #16](https://github.com/D3M80L/hassio-mipow/pull/16) seit Januar 2025 bereit, über ein Jahr lang von mehreren unabhängigen Nutzern als funktionierend bestätigt, aber nie gemergt.

Dieser Fork übernimmt genau diesen Fix (plus die dazugehörige `TIME_MINUTES`-Deprecation aus [Issue #17](https://github.com/D3M80L/hassio-mipow/issues/17) und eine RSSI-API-Änderung im modernen Bluetooth-Stack) und hält die Integration am Laufen.

## Unterstützte Geräte

- BTL300
- BTL305ES
- BTL200/BTL201
- Da das MiPow-Protokoll geräteübergreifend verwendet wird, sollten auch andere MiPow-LED-Geräte funktionieren.

## Was die Integration kann

Benötigt die [Home-Assistant-Bluetooth-Integration](https://www.home-assistant.io/integrations/bluetooth/). Geräte werden automatisch erkannt oder lassen sich manuell über die Integrationsliste hinzufügen.

### Farblicht
Weißwert und Farbe lassen sich getrennt steuern. Ist eine Farbe gewählt, ändert die Helligkeit nur die Farbe; ohne Farbauswahl steuert die Helligkeit den Weißwert.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/color_palette.png" alt="Beispiel Farbpalette">
</p>

### Nur Weißlicht
In diesem Modus wird nur der Weißwert geändert, Farben werden entfernt.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/white_mode.png" alt="Beispiel Weißlicht-Modus">
</p>

### Batteriesensor
Für batteriebetriebene Geräte steht ein Batteriesensor zur Verfügung.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/battery.png" alt="Batteriesensor">
</p>

### Effekt-Steuerung
Die eingebauten Effekte lassen sich konfigurieren:
- **delay** — je niedriger der Wert, desto langsamer der Effekt
- **repetitions** — wie oft der Effekt wiederholt wird
- **pause** — nach den Wiederholungen schaltet sich das Licht aus, der Effekt startet danach erneut

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/effect_control.png" alt="Effekt-Steuerung">
</p>

Vordefinierte Effekte, dargestellt in HA als:
- light (kein Effekt)
- flash
- pulse
- rainbow
- colorloop
- candle

### Timer
<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/timer.png" alt="Timer-Steuerung">
</p>

Manche Geräte unterstützen einen Timer, der das Gerät nach einer festgelegten Anzahl Minuten ausschaltet — nützlich, um batteriebetriebene Geräte auch außerhalb der HA-Kontrolle sicher abzuschalten. Das Steuern über HA bleibt trotzdem empfohlen.

## Installation

### HACS (empfohlen)

1. In HACS das Drei-Punkte-Menü öffnen → **Custom repositories**.
2. `https://github.com/dhaucke/hassio-mipow` als Typ **Integration** hinzufügen.
3. **MiPow** installieren und Home Assistant neu starten.

### Manuell

- Den Ordner `custom_components/mipow` aus diesem Repo in dein Home-Assistant-Verzeichnis `custom_components/mipow` kopieren.
- Home Assistant neu starten.

## Support

Dies ist ein kleiner, unbezahlter Fork, der gepflegt wird, um einen echten, seit Langem bekannten Bug zu beheben, den das Original nie gemergt hat — kein finanziertes oder im Team betreutes Projekt.

- [Issues](https://github.com/dhaucke/hassio-mipow/issues)

## Haftungsausschluss

Dieses Paket und sein Autor stehen in keiner Verbindung zu MiPow. Nutzung auf eigene Gefahr.

## Lizenz

Veröffentlicht unter der MIT-Lizenz. Der ursprüngliche Copyright-Hinweis von [D3M80L/hassio-mipow](https://github.com/D3M80L/hassio-mipow) ist in [LICENSE](LICENSE) und in der Projekthistorie erhalten.

---

# English

## Why this fork exists

This is a fork of [D3M80L/hassio-mipow](https://github.com/D3M80L/hassio-mipow). It's been a while since the original maintainer's last commit, and since then the integration has been completely broken on current Home Assistant: `ModuleNotFoundError: No module named 'homeassistant.backports.enum'` (see [issue #18](https://github.com/D3M80L/hassio-mipow/issues/18)) - HA removed that backport module. A working fix has sat as [PR #16](https://github.com/D3M80L/hassio-mipow/pull/16) since January 2025, confirmed working by multiple independent users over more than a year, but never merged.

This fork adopts that exact fix (plus the related `TIME_MINUTES` deprecation from [issue #17](https://github.com/D3M80L/hassio-mipow/issues/17) and an RSSI API change in the modern Bluetooth stack) and keeps the integration running.

## Verified devices

- BTL300
- BTL305ES
- BTL200/BTL201
- Since the MiPow protocol is used across other MiPow LED devices, the integration should also support those.

## What this integration does

Requires the [Home Assistant Bluetooth integration](https://www.home-assistant.io/integrations/bluetooth/). Devices are discovered automatically, or can be added manually from the integrations list.

### Color light
White value and color can be controlled separately. When a color is selected, brightness only changes the color; without a color selected, brightness controls the white value.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/color_palette.png" alt="Example color palette">
</p>

### White light only
In this mode only the white value changes; any colors are removed.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/white_mode.png" alt="Example white color mode">
</p>

### Battery sensor
A battery sensor is available for battery-powered devices.

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/battery.png" alt="Battery sensor">
</p>

### Effect configuration
The built-in effects can be controlled:
- **delay** - the lower the value, the slower the effect
- **repetitions** - how many times the effect repeats
- **pause** - after repetitions, the light turns off, then the effect repeats

<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/effect_control.png" alt="Effect controls">
</p>

Predefined effects, represented in HA as:
- light (no effect)
- flash
- pulse
- rainbow
- colorloop
- candle

### Timer
<p align="center" width="100%">
  <img src="https://raw.githubusercontent.com/dhaucke/hassio-mipow/main/doc/timer.png" alt="Timer control">
</p>

Some devices support a timer that turns the device off after a specified number of minutes - useful to ensure battery-powered devices turn off even outside HA's control. Controlling the device from HA is still recommended.

## Installation

### HACS (preferred)

1. In HACS, open the three-dot menu → **Custom repositories**.
2. Add `https://github.com/dhaucke/hassio-mipow` as type **Integration**.
3. Install **MiPow** and restart Home Assistant.

### Manual

- Copy `custom_components/mipow` from this repo into your Home Assistant `custom_components/mipow`.
- Restart Home Assistant.

## Support

This is a small, unpaid fork maintained to fix one real, long-known bug the original never merged - not a funded or team-maintained project.

- [Issues](https://github.com/dhaucke/hassio-mipow/issues)

## Disclaimer

This package and its author are not affiliated with MiPow. Use at your own risk.

## License

Released under the MIT license. The original copyright notice from [D3M80L/hassio-mipow](https://github.com/D3M80L/hassio-mipow) is preserved in [LICENSE](LICENSE) and in the project history.
