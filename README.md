# ThinkCentre M910X Hackintosh OpenCore EFI

[![macOS](https://img.shields.io/badge/macOS-Ventura-brightgreen.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.9.5-blue)](https://github.com/acidanthera/OpenCorePkg)
[![Status](https://img.shields.io/badge/Status-As--Is-orange)](#as-is-statement)

**English** | [简体中文](README_CN.md)

> **As-Is Statement**: This EFI configuration has been operating stably with OpenCore 0.9.5 and macOS Ventura 13.5.2 for over 1.5 years. The repository is provided **As-Is** with no active maintenance or future updates planned. It is intended for experienced Hackintosh users seeking reference or baseline configurations.

---

> ⚠️ **IMPORTANT**: **Generate and replace your own System Serial Numbers (SSN, Board Serial / MLB, SmUUID, ROM)** in `config.plist` before booting for the first time!

---

## Table of Contents
- [1. EFI Configurations & Hardware Variants](#1-efi-configurations--hardware-variants)
  - [1.1 Macmini 8,1 (iGPU Only)](#11-macmini-81-igpu-only)
  - [1.2 iMac 18,3 (dGPU + iGPU)](#12-imac-183-dgpu--igpu)
- [2. Key BIOS Settings](#2-key-bios-settings)
- [3. Operational Status](#3-operational-status)
- [4. Screenshots](#4-screenshots)
- [5. Credits & References](#5-credits--references)

---

## 1. EFI Configurations & Hardware Variants

This repository provides two distinct OpenCore EFI configurations for Lenovo ThinkCentre M910X Tiny:

| Directory | Target Model | Hardware Focus | Description |
| :--- | :--- | :--- | :--- |
| [`MacMini with iGPU/EFI`](./MacMini%20with%20iGPU/EFI) | `Macmini8,1` | Intel HD 630 (iGPU) | For models without a discrete GPU or when dGPU is disabled. |
| [`iMac with dGPU/EFI`](./iMac%20with%20dGPU/EFI) | `iMac18,3` | AMD RX460/RX560 + HD 630 | For models equipped with a low-profile AMD dGPU, with iGPU enabled for compute tasks. |

---

### 1.1 Macmini 8,1 (iGPU Only)

Designed for Intel Kaby Lake 7th-Gen CPUs without a discrete GPU, utilizing `Macmini8,1` SMBIOS for optimized power management.

#### Hardware Specifications

| Component | Specification | Note |
| :--- | :--- | :--- |
| **Model** | Lenovo ThinkCentre M910X Tiny | |
| **Motherboard** | Lenovo Intel Q270 | |
| **CPU** | Intel Core i5-7500T | Low-power desktop CPU |
| **iGPU** | Intel HD Graphics 630 | Display output |
| **Storage** | WD SN730 512GB | M.2 NVMe |
| **RAM** | 16GB (DDR4 3200 8GB * 2) | Operating at 2400MHz |
| **WLAN & BT** | Broadcom BCM94360CS2 | Native Apple card, plug-and-play |
| **Power Supply** | 90W ThinkCentre DC Adapter | |

---

### 1.2 iMac 18,3 (dGPU + iGPU)

Combines desktop Intel HD 630 (headless/compute-only) with a native AMD RX460/RX560 dGPU, mapped with `iMac18,3` SMBIOS.

#### Hardware Specifications

| Component | Specification | Note |
| :--- | :--- | :--- |
| **Model** | Lenovo ThinkCentre M910X Tiny | |
| **Motherboard** | Lenovo Intel Q270 | |
| **CPU** | Intel Core i5-7500T | Low-power desktop CPU |
| **iGPU** | Intel HD Graphics 630 | Set to Headless / Compute-Only |
| **dGPU** | AMD Radeon RX460 4GB | Native macOS support |
| **Storage** | WD SN730 512GB | M.2 NVMe |
| **RAM** | 16GB (DDR4 3200 8GB * 2) | |
| **WLAN & BT** | Broadcom BCM94360CS2 | Native Apple card, plug-and-play |
| **Power Supply** | 90W ThinkCentre DC Adapter | |

---

## 2. Key BIOS Settings

Access Lenovo BIOS (`F1` at startup) and set the following essential parameters:

| Category | BIOS Option | Setting | Note |
| :--- | :--- | :--- | :--- |
| **Security** | Secure Boot | **Disabled** | Mandatory |
| **Devices -> Video** | Primary Display | **IGPU** *(Macmini)* / **PEG** *(iMac)* | Select default video port |
| **CPU / Hardware** | VT-d | **Disabled** (or keep `DisableIoMapper=True` in config) | Prevents I/O map crashes |
| **Startup** | Fast Boot | **Disabled** | Disable fast startup |

---

## 3. Operational Status

All core macOS features function out of the box with the matching hardware:

- [x] Full QE/CI Hardware Graphics Acceleration (Intel HD 630 & AMD RX460)
- [x] Mini DP Output on dGPU & HiDPI (4K Resolution)
- [x] Audio over DisplayPort & 3.5mm Headphone Jack / Internal Mic
- [x] Customized USB Map (All 6 USB ports functioning)
- [x] Wi-Fi & Bluetooth (AirDrop, AirPlay, Continuity, Handoff)
- [x] Native CPU Power Management & Sleep / Wake

---

## 4. Screenshots

### Device Info
![device info](./imgs/iMac/device%20info.png)

### HiDPI & Sidecar
![HiDPI](./imgs/iMac/HiDPI.png)

### Bluetooth
![bluetooth](./imgs/iMac/bluetooth.png)

### AirDrop
![airdrop](./imgs/iMac/airdrop.png)

### dGPU (AMD RX460)
![GPU](./imgs/iMac/gpu.png)

### Dual GPUs (iGPU & dGPU)
![iGPU and dGPU](./imgs/iMac/igpu.png)

---

## 5. Credits & References

- Built upon the [Acidanthera OpenCore](https://github.com/acidanthera/OpenCorePkg) bootloader. Special thanks to all open-source Hackintosh contributors!
