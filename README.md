# Astral Pool Viron eQuilibrium Chlorinator

[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE)

[![hacs][hacsbadge]][hacs]
[![Project Maintenance][maintenance-shield]][user_profile]

[![Community Forum][forum-shield]][forum]

## About

This is a fork of [@pbutterworth](https://github.com/pbutterworth)'s [astralpool_chlorinator](https://github.com/pbutterworth/astralpool_chlorinator) integration. It uses my forked [pychlorinator](https://github.com/kesawi/pychlorinator) library. Full credit to pbutterworth for the original work and protocol reverse engineering.

## Platforms

| Platform        | Description                                                               |
| --------------- | ------------------------------------------------------------------------- |
| `binary_sensor` | Pump running, cell running, pump priming, chemistry values valid/current, sanitising status. |
| `sensor`        | pH, pH setpoint, ORP setpoint, mode, pump speed, chlorine status, info message, pH/ORP control type, cell running time, cell reversal count, low salt cell running time, previous day cell load, acid dosing inhibit status and time remaining, highest/lowest pH and ORP measured. |
| `select`        | Control chlorinator mode (off/auto/manual), pump speed, and default manual speed. |
| `number`        | Set pH setpoint, chlorine output level (0-8 manual / ORP mV automatic), and acid dosing inhibit period (0-1440 min). |
| `button`        | Dismiss info message, disable/re-enable acid dosing, reset statistics, trigger cell reversal. |

## Requirements

- A Bluetooth proxy (e.g. ESP32 running ESPHome bluetooth_proxy) within range of the chlorinator
- Home Assistant with HACS installed

## Installation via HACS

1. In HACS, go to **Integrations → Custom Repositories**
2. Add `https://github.com/kesawi/astralpool_chlorinator` as an **Integration**
3. Install **Astral Pool Viron eQuilibrium Chlorinator**
4. Restart Home Assistant
5. The chlorinator will be auto-discovered via Bluetooth

## Access Token

The access token is the 4-digit Bluetooth access code found on the chlorinator's Bluetooth install screen:
- On the chlorinator front panel, navigate to **Install → Bluetooth Install**
- The 4-digit code will be displayed

## Configuration is done in the UI

After installation, the poll interval can be configured via:
**Settings → Integrations → Astral Pool → ⚙️ Configure**

| Setting | Description | Default | Range |
| ------- | ----------- | ------- | ----- |
| Poll Interval (seconds) | How frequently the integration connects via Bluetooth to read device state. Setting too low may cause connection issues. | 60 | 10-300 |

## Notes

- ORP probe disconnection: if your ORP probe has ground loop issues, disconnect it and set the chlorine output to manual (0–8 scale) via the Chlorine Output number entity
- Acid dosing re-enable: sending DisableAcidDosingForPeriod with period=0 is used as the cancel mechanism — verify this works with your specific unit
- BLE connection lock prevents concurrent read/write operations
- Cell running time sensors are reported in hours
- Time sync is not yet supported — potential future enhancement
- Only tested on Viron EQ25

## Credits

Originally developed by [@pbutterworth](https://github.com/pbutterworth). This is a fork maintained by [@kesawi](https://github.com/kesawi).

## Related

- [@pbutterworth](https://github.com/pbutterworth)'s [astralpool_chlorinator](https://github.com/pbutterworth/astralpool_chlorinator) — original integration
- [@pbutterworth](https://github.com/pbutterworth)'s [pychlorinator](https://github.com/pbutterworth/pychlorinator) — original BLE library
- [@kesawi](https://github.com/kesawi)'s [pychlorinator](https://github.com/kesawi/pychlorinator) — forked BLE library used by this integration

---

[commits-shield]: https://img.shields.io/github/commit-activity/y/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[commits]: https://github.com/kesawi/astralpool_chlorinator/commits/main
[hacs]: https://hacs.xyz
[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[forum]: https://community.home-assistant.io/
[license-shield]: https://img.shields.io/github/license/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-%40kesawi-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[releases]: https://github.com/kesawi/astralpool_chlorinator/releases
[user_profile]: https://github.com/kesawi