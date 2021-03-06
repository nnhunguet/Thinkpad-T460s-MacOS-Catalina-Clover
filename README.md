# Thinkpad T460s MacOS Catalina with Clover Bootloader
# [my original OpenCore build is live! go check it out](https://github.com/simprecicchiani/Thinkpad-T460s-macOS-OpenCore)

> I know this page is way too long but it has many informations I personally would like to know when looking into someone's EFI

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

## What's different from others T460s configs on GitHub

- **VirtualSMC** is used over FakeSMC and ACPIBatteryManager
> Huge improvement for stability and reliability, battery management is perfect
- No additional ketxs for semi-supported WLAN cards
> BCM94360CS2 is a genuine Macbook Air card and it's supported out-of-the-box
- **VoodooPS2** by Acidanthera for trackpad gestures and **physical buttons**

## Recomended changes for 100% Macbook experience

- Use [one-key-hidpi](https://github.com/xzhih/one-key-hidpi) to enable HiDPI
- Change `SMBIOS -> Board Serial Number and System Serial Number` to enable iCloud account related features
- Set `Boot -> Default Boot Volume` to volume's name itself
- Check flag `Boot -> Fast`

## Tips for MacOS

- Make dock animation faster and zero delay
```
defaults write com.apple.dock autohide-delay -float 0
defaults write com.apple.dock autohide-time-modifier -float 0.5
killall Dock
```
- Mount EFI
```
sudo diskutil list
sudo diskutil mount /dev/diskNsN
```
- Enable HiDPI
```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"
```
- Monitor temperatures and power consumption with [HWMonitor](https://github.com/kzlekk/HWSensors/releases)
> I know it's old and no longer supported, but it gets the job done and i really like the design

## Bios settings

- `Security -> Security Chip` **Disabled**
- `Memory Protection -> Execution Prevention` **Enabled**
- `Virtualization -> Intel Virtualization Technology` **Disabled**
- `Virtualization -> Intel VT-d Feature` **Enabled**
- `Anti-Theft -> Current Setting` **Disabled**
- `Anti-Theft -> Computrace -> Current Setting` **Disabled**
- `Secure Boot -> Secure Boot` **Disabled**
- `Intel SGX -> Intel SGX Control` **Disabled**
- `Device Guard` **Disabled**
- `UEFI/Legacy Boot` **UEFI Only**
- `CSM Support` **No**

## What works

>Boot time from Clover to Desktop is 28s
- Sleep / Wake
- Wifi and Bluetooth (BCM94360CS2)
- **Handoff, Continuity, AirDrop, Sidecar ([wireless](https://www.youtube.com/watch?v=D5yButavaWY))**
- iMessage, FaceTime, App Store, iTunes Store **(change SMBIOS values)**
- Ethernet
- Onboard audio
- All USB 3.0 ports
- Battery **(very stable and precise capacity tracking)**
- Trackpad, Trackpoint, gestures and finally **physical buttons**
- miniDP and HDMI

## What doesn't work
> If you have any questions or suggestions feel free to contact me
- SD Card Reader
- Fingerprint Reader
- SIP is disabled and FileVault isn't tested

## Update tracker

```
MacOS: 10.15.4
Clover: r5107
Lilu: 1.4.3
VirtualSMC: 1.1.1
WhateverGreen: 1.3.8
AppleALC: 1.4.8
VoodooPS2Controller: 2.1.3
USBInjectAll: 0.7.1
IntelMausi: 1.0.2
```

## Thanks to

All the hackintosh community, in particular you guys on GitHub.
