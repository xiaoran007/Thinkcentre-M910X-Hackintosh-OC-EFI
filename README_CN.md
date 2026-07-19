# ThinkCentre M910X Hackintosh OpenCore EFI

[![macOS](https://img.shields.io/badge/macOS-Ventura-brightgreen.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.9.5-blue)](https://github.com/acidanthera/OpenCorePkg)
[![Status](https://img.shields.io/badge/Status-As--Is-orange)](#声明--as-is-statement)

[English](README.md) | **简体中文**

> **状态声明**：本项目 EFI 在 OpenCore 0.9.5 及 macOS Ventura 13.5.2 环境下稳定工作超过 1.5 年。项目目前处于 **As-Is（按现状提供）** 状态，不再提供后续维护或新版本支持。适合具备黑苹果经验的使用者检索与参考。

---

> ⚠️ **重要提示**：在首次引导前，**务必自行修改并替换三码（Serial Number, Board Serial / MLB, SmUUID, ROM）**！

---

## 目录
- [1. 机型与配置分类](#1-机型与配置分类)
  - [1.1 Macmini 8,1（纯核显模式）](#11-macmini-81纯核显模式)
  - [1.2 iMac 18,3（独显+核显模式）](#12-imac-183独显核显模式)
- [2. BIOS 关键设置](#2-bios-关键设置)
- [3. 运行状态](#3-运行状态)
- [4. 效果截图](#4-效果截图)
- [5. 致谢与参考](#5-致谢与参考)

---

## 1. 机型与配置分类

本项目针对联想 ThinkCentre M910X Tiny 提供两套 OpenCore EFI 配置：

| 目录路径 | 目标机型 | 适配硬件 | 说明 |
| :--- | :--- | :--- | :--- |
| [`MacMini with iGPU/EFI`](./MacMini%20with%20iGPU/EFI) | `Macmini8,1` | Intel HD 630 (核显) | 适合无独显版本或不计划使用独显的设备，默认已屏蔽独显。 |
| [`iMac with dGPU/EFI`](./iMac%20with%20dGPU/EFI) | `iMac18,3` | AMD RX460/RX560 + HD 630 | 适合搭载半高独显卡（如 AMD RX460/RX560）的设备，核显开启计算加速。 |

---

### 1.1 Macmini 8,1（纯核显模式）

基于 Intel Kaby Lake 7 代处理器，在无独显/屏蔽独显配置下选用 `Macmini8,1` SMBIOS 获得最佳电源管理。

#### 硬件规格

| 硬件项 | 型号规格 | 备注 |
| :--- | :--- | :--- |
| **设备** | Lenovo ThinkCentre M910X Tiny | |
| **主板** | Lenovo Intel Q270 | |
| **CPU** | Intel Core i5-7500T | 低功耗桌面 CPU |
| **核显 (iGPU)** | Intel HD Graphics 630 | 显示输出 |
| **硬盘** | WD SN730 512GB | M.2 NVMe |
| **内存** | 16GB (DDR4 3200 8GB * 2) | 运行在 2400MHz 频段 |
| **无线网卡** | Broadcom BCM94360CS2 | Apple 原装拆机卡，免驱 |
| **电源适配器** | 90W ThinkCentre 黄金针直流电源 | |

---

### 1.2 iMac 18,3（独显+核显模式）

结合桌面级 Intel HD 630 (仅计算) 与 AMD RX460/RX560 免驱独立显卡，搭配 `iMac18,3` SMBIOS。

#### 硬件规格

| 硬件项 | 型号规格 | 备注 |
| :--- | :--- | :--- |
| **设备** | Lenovo ThinkCentre M910X Tiny | |
| **主板** | Lenovo Intel Q270 | |
| **CPU** | Intel Core i5-7500T | 低功耗桌面 CPU |
| **核显 (iGPU)** | Intel HD Graphics 630 | 设置为仅计算 (Compute Only) |
| **独显 (dGPU)** | AMD Radeon RX460 4GB | 对应 Apple 官方原生支持架构，免驱 |
| **硬盘** | WD SN730 512GB | M.2 NVMe |
| **内存** | 16GB (DDR4 3200 8GB * 2) | |
| **无线网卡** | Broadcom BCM94360CS2 | Apple 原装拆机卡，免驱 |
| **电源适配器** | 90W ThinkCentre 直流电源 | |

---

## 2. BIOS 关键设置

进入 Lenovo BIOS (启动按 `F1`) 调整以下核心选项：

| 选项分类 | 设置项 | 推荐值 | 补充说明 |
| :--- | :--- | :--- | :--- |
| **Security** | Secure Boot | **Disabled** | 必须关闭 |
| **Devices -> Video** | Primary Display | **IGPU** *(Macmini版)* / **PEG** *(iMac版)* | 决定默认画面输出接口 |
| **CPU / Hardware** | VT-d | **Disabled** 或开启 `DisableIoMapper` | 避免 I/O 映射异常 |
| **Startup** | Fast Boot | **Disabled** | 关闭快速启动 |

---

## 3. 运行状态

得益于良好的硬件匹配度，系统大部分核心功能均已完美驱动：

- [x] Intel HD630 与 AMD RX460 完整的 QE/CI 硬件图形加速
- [x] 独显 Mini DP 接口输出 & HiDPI (4K 输出)
- [x] DisplayPort 音频输出 & 3.5mm 耳机/板载麦克风
- [x] USB 端口定制（全部 6 个 USB 端口工作正常）
- [x] Wi-Fi 与 蓝牙（隔空投送 Airdrop / 隔空播放 AirPlay / 接力 Continuity 等接续功能正常）
- [x] CPU 电源管理与原生睡眠唤醒

---

## 4. 效果截图

### 设备信息 (Device Info)
![device info](./imgs/iMac/device%20info.png)

### HiDPI & 随航 (HiDPI & Sidecar)
![HiDPI](./imgs/iMac/HiDPI.png)

### 蓝牙 (Bluetooth)
![bluetooth](./imgs/iMac/bluetooth.png)

### 隔空投送 (AirDrop)
![airdrop](./imgs/iMac/airdrop.png)

### 独显 (dGPU RX460)
![GPU](./imgs/iMac/gpu.png)

### 协同双显卡 (iGPU & dGPU)
![iGPU and dGPU](./imgs/iMac/igpu.png)

---

## 5. 致谢与参考

- 本项目 EFI 核心框架基于 [Acidanthera OpenCore](https://github.com/acidanthera/OpenCorePkg) 构建。感谢所有黑苹果开源社区开发者们的无私奉献！
