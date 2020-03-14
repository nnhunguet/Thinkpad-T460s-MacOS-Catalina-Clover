# Thinkpad T460s MacOS Catalina with Clover Bootloader

## Introduction

EFI for Thinkpad T460s (20F9003AUS)

- Processor: Intel Core i7-6600U (2C, 2.6 / 3.4GHz, 4MB)vPro
- Graphics: Integrated Intel HD Graphics 520
- Memory: 4GB Soldered + 4GB DIMM
- Display: 14" WQHD (2560x1440) IPS
- Sound Card: Realtek ALC293
- Multi-touch: None
- Storage: 256GB SSD M.2 Opal2
- Optical: None
- WLAN + Bluetooth: ~~Intel 8260 ac, 2x2 + BT4.1~~ **replaced by BCM94360CS2 with NGFF adapter**
- WWAN: WWAN Upgradable (Legacy_Sierra_QMI.kext needed, not tested but should work)
- Smart Card Reader: None
- Camera: 720p
- Keyboard: Backlit
- Fingerprint Reader: Yes
- Battery: 3-cell (23Wh) + 3-cell (26Wh)

## Bios

- `Security -> Security Chip`: **Disabled**;
- `Memory Protection -> Execution Prevention`: **Enabled**;
- `Virtualization -> Intel Virtualization Technology`: **Enabled**;
- `Internal Device Access -> Bottom Cover Tamper Detection`: must be **Disabled**;
- `Anti-Theft -> Current Setting`: **Disabled**;
- `Anti-Theft -> Computrace -> Current Setting`: **Disabled**;
- `Secure Boot -> Secure Boot`: **Disabled**;
- `UEFI/Legacy Boot`: **UEFI Only**;
- `CSM Support`: **No**.

## What works

- Sleep / Wake
- Wifi and Bluetooth (BCM94360CS2)
- **Handoff, Continuity, AirDrop, Sidecar (wireless)**
- iMessage, FaceTime, App Store, iTunes Store **(change SMBIOS -> MLB and SystemSerialNumber)**
- Ethernet
- Onboard audio
- USB 2.0 / USB 3.0
- Battery **very stable and precise capacity left**
- Trackpad
- Trackpoint
- miniDP and HDMI
- Use [one-key-hidpi](https://github.com/xzhih/one-key-hidpi) to enable HiDPI

## What doesn't work

- SD Card Reader
- Trackpad fisical buttons
- Fingerprint Reader

## Thanks to

All the hackintosh community, in particular you guys on GitHub 
