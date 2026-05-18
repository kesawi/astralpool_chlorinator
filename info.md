[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]][license]

[![hacs][hacsbadge]][hacs]
[![Project Maintenance][maintenance-shield]][user_profile]

[![Community Forum][forum-shield]][forum]

**This component will set up the following platforms.**

| Platform        | Description                                                               |
| --------------- | ------------------------------------------------------------------------- |
| `binary_sensor` | Pump running, cell running, pump priming, chemistry values valid/current, sanitising status. |
| `sensor`        | pH, pH setpoint, ORP setpoint, mode, pump speed, chlorine status, info message, pH/ORP control type, cell running time, cell reversal count, low salt cell running time, previous day cell load, acid dosing inhibit status and time remaining, highest/lowest pH and ORP measured. |
| `select`        | Control chlorinator mode (off/auto/manual), pump speed, and default manual speed. |
| `number`        | Set pH setpoint, chlorine output level (0-8 manual / ORP mV automatic), and acid dosing inhibit period (0-1440 min). |
| `button`        | Dismiss info message, disable/re-enable acid dosing, reset statistics, trigger cell reversal. |

{% if not installed %}

## Installation

1. Click install.
2. Restart Home Assistant.
3. Home Assistant will now discover chlorinators in Bluetooth range that are advertising the right BLE UUID.

{% endif %}

## Requirements

A Bluetooth proxy (e.g. ESP32 running ESPHome bluetooth_proxy) within range of the chlorinator.

## Configuration is done in the UI

After installation, the poll interval can be configured via **Settings → Integrations → Astral Pool → ⚙️ Configure**. Range: 10-300 seconds, default: 60 seconds. Setting too low may cause BLE connection issues.

## Credits

Originally developed by [@pbutterworth](https://github.com/pbutterworth). This is a fork maintained by [@kesawi](https://github.com/kesawi).

---

[commits-shield]: https://img.shields.io/github/commit-activity/y/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[commits]: https://github.com/kesawi/astralpool_chlorinator/commits/main
[hacs]: https://hacs.xyz
[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[forum]: https://community.home-assistant.io/
[license]: https://github.com/kesawi/astralpool_chlorinator/blob/main/LICENSE
[license-shield]: https://img.shields.io/github/license/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-%40kesawi-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/kesawi/astralpool_chlorinator.svg?style=for-the-badge
[releases]: https://github.com/kesawi/astralpool_chlorinator/releases
[user_profile]: https://github.com/kesawi