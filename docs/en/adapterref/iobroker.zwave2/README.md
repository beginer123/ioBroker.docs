![Logo](admin/zwave2.svg)

# ioBroker.zwave2

[![node](https://img.shields.io/node/v/iobroker.zwave2.svg)
![npm](https://img.shields.io/npm/v/iobroker.zwave2.svg)](https://www.npmjs.com/package/iobroker.zwave2)
[![changelog](https://img.shields.io/badge/read-Changelog-informational)](CHANGELOG.md)

![Number of Installations](http://iobroker.live/badges/zwave2-installed.svg)
![Number of Installations](http://iobroker.live/badges/zwave2-stable.svg)

![Test and Release](https://github.com/AlCalzone/iobroker.zwave2/workflows/Test%20and%20Release/badge.svg)
[![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/AlCalzone/ioBroker.zwave2.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/AlCalzone/ioBroker.zwave2/context:javascript)

<h2 align="center">Z-Wave for ioBroker. But better.</h3>

Z-Wave 2 is a brand new Z-Wave implementation for ioBroker. It is based on [`zwave-js`](https://github.com/AlCalzone/node-zwave-js), which was written from the ground up for your benefit.

Unless [`ioBroker.zwave`](https://github.com/ioBroker/ioBroker.zwave/) it does not require `OpenZWave`. This means that the installation and updates are fast, and no compilation of static libraries and other complicated steps are necessary.

Furthermore, some devices just don't work in the original adapter, e.g. the Fibaro Roller Shutter 3.

Easy usage in ioBroker was kept in mind during the whole development. For example, some devices reuse configuration parameters to configure many different things. In this adapter, most of them are split into separate states and no complicated math is necessary:
| Config params in ioBroker.zwave2 | vs | Config params in ioBroker.zwave |
| --- | --- | --- |
| ![](docs/de/images/config-params.png) | vs | ![](docs/de/images/config-params-legacy.png) |

---

## Documentation and usage
* [FAQ](docs/en/FAQ.md)
* [Troubleshooting](docs/en/troubleshooting.md) · [bei Problemen](docs/de/bei-problemen.md)

---

## Changelog
[Older changes](CHANGELOG_OLD.md)
<!--
	Placeholder for next versions:
	### __WORK IN PROGRESS__
-->

### 1.8.2 (2020-12-23)
* When a node does not respond because it is asleep, the message is no longer discarded. This should improve the interview behavior of sleeping nodes.
* Added new config files
* Fixed wrong label and description for Z-Wave.Me UZB
* Added missing label to Binary Sensor CC
* Added missing % unit to Battery level
* The `targetValue` for the `Binary Switch`, `Multilevel Switch` and `Basic` CCs is no longer removed when a report without one is received
* Some more interview timeouts are ignored

### 1.8.1 (2020-12-14)
* The `targetValue` of switch-type CCs is no longer overwritten with `undefined` when a report without target value is received
* Added a config file for `Jasco ZW3010`
* Added a config file for `HeatIt Z-TRM3`
* Added a config file for `Eurotronic Air quality sensor (Luftgütesensor)`
* Improved support for `Qubino Flush 2 Relay`
* The `Multi Channel Association CC`, `Z-Wave+ CC` and `Node Naming and Location CC` values are now hidden
* `Color Switch CC`: Setting the **warm white** `targetValue` no longer falsely claims that the `propertyKey` is missing
* Removed some debug logging which could blow up the log file size
* Removing a node association no longer throws an error when both multi channel and normal associations are supported.
* `Notification CC Reports` are now parsed correctly when the `V1 Alarm` bytes are not zero
* Added support for `*.gbl` firmware files and Aeotec updater executables which include a checksum and a target chip byte.
* Fixed an issue where the wrong response could be mapped to some commands
* ... and some more minor bugfixes

### 1.8.0 (2020-11-14)
* Improved config files for Fibaro Keyfob (no special chars anymore) and Shenzhen Neo PD03Z
* Non-critical steps during the interview of `Central Scene CC`, `Configuration CC V3+` and `Association Group Info CC` are now skipped when the node does not respond or responds incorrectly
* Multi Channel Lifeline Associations are no longer created automatically if the device does not support the `Multi Channel CC` - this should fix compatibility with most Qubino devices
* Fixed an issue where marking nodes with active transaction as asleep would mess up the serial communication with the controller
* Empty user codes are now also handled as strings instead of Buffer objects
* The `targetValue` property for the `Binary Switch`, `Multilevel Switch` and `Basic` CCs is now created even if it has no value
* Values for Notification events (one-time events) are now created. Previously only Notification variables were available as states

### 1.7.10 (2020-11-04)
* Improved compatibility with devices that don't follow the `User Code CC` and `Notification CC` specifications correctly (like Zipato Keypad)
* Added the ability to edit binary values (e.g. RFID codes) using hexadecimal strings, e.g. `0xbada55`.

### 1.7.9 (2020-11-01)
* Fixed a crash in the adapter settings when a node's device type is not yet set

## License

MIT License

Copyright (c) 2019-2020 AlCalzone

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
