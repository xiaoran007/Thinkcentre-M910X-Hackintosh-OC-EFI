# Thinkcentre-M910X-Hackintosh-OC-EFI
## OpenCore version 0.9.5
[![macOS](https://img.shields.io/badge/macOS-Monterey-brightgreen.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![macOS](https://img.shields.io/badge/macOS-Ventura-brightgreen.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![macOS](https://img.shields.io/badge/macOS-Sonoma-brightgreen.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.9.5-blue)](https://github.com/acidanthera/OpenCorePkg)

**这个EFI在OC 0.9.5 与 macOS 13.5.2稳定工作超过1.5年！**

**This EFI has worked stably for over 1.5 years with OC 0.9.5 and macOS 13.5.2！**

# ⚠️ Change System code(SSN,UUID,ROM) FIRST.
# ⚠️ 务必修改三码(SSN,UUID,ROM)

# index | 索引
- [Suggestion | 建议](#suggestion--建议)
- [compatibilities ｜ 兼容性](#compatibilities--兼容性)
- [operational state ｜ 运行状态](#operational-state--运行状态)
    * [Working](#working)
    * [Not working](#not-working)
    * [Not tested yet](#not-tested-yet)
- [0. File index | 文件索引](#0-file-index--文件索引)
- [1. Hackintosh type | 设备类型](#1-hackintosh-type--设备类型)
    * [1.1 Macmini 8, 1](#11-macmini-8-1)
    * [1.2 iMac 18, 3](#12-imac-18-3)
- [2. Installation guideline | 安装指引](#2-installation-guideline--安装指引)


## Suggestion | 建议
如果你的m910x主机是独显版本，请优先考虑使用iMac版的EFI，参阅[1.2章节](#12-imac-18-3)。如果你不想使用独立显卡，可使用Mac mini版EFI（[1.1章节](#11-macmini-8-1)），该版本EFI已默认屏蔽独立显卡，请在BIOS中设置主显示输出为核显。

如果你的m910x主机是无独显的版本（通常搭配2.5寸硬盘出售），则只能使用Mac mini版的EFI，参阅[1.1章节](#11-macmini-8-1)。如果你想使用独显，可以购买免驱显卡自行安装并使用iMac版EFI（[1.2章节](#12-imac-18-3)）替换当前EFI。

If your m910x has a discrete GPU, please prioritize using the iMac version of EFI, see [section 1.2](#12-imac-18-3). If you don't want to use discrete GPU, you can use the Mac mini version of EFI ([Section 1.1](#11-macmini-8-1)), which has blocked the discrete graphics card by default, please set the main display output to iGPU in BIOS.

If your m910x doesn't have discrete graphics (usually sold with a 2.5” hard disk), you can only use the Mac mini version of EFI, see [section 1.1](#11-macmini-8-1). If you want to use a dGPU, you can buy a drive-free graphics card and install it yourself and replace the current EFI with the iMac version of the EFI ([Section 1.2](#12-imac-18-3)).

## compatibilities ｜ 兼容性
EFI基于m910x测试功能完备，如需了解测试时使用的完整硬件信息，请参阅1.1和1.2章节中的硬件部分。

使用Q270主板 + 7代处理器的设备理论上均可直接使用EFI引导而不需要专门设置，如使用intel无线网卡请添加相关驱动。

EFI is fully functional based on the test, for complete information on the hardware used in the test, please refer to the hardware section in sections 1.1 and 1.2.

Devices using Q270 motherboards + 7th generation processors can theoretically boot directly with this EFI without special setup, but if using an intel wireless card, please add the relevant drivers.

## operational state ｜ 运行状态
### Working：

- Mini DP ports on RX460  
- HiDpi with 4K output
- Audio output on DP  
- All USB ports  
- Wi-Fi & Bluetooth  
- 3.5mm Audio Jack and Internal Mic
- Airdrop  
- AirPlay  
- Continuity  
- QE/CI of Intel UHD 630 & rx460
- CPU Power Management
- Sleep 

### Not working:

- None

### Not tested yet:

- None 

### some imgs:

#### device information | 设备信息
![device info](./imgs/iMac/device%20info.png)

#### HiDpi and Sidecar | HiDpi和随航
![HiDpi](./imgs/iMac/HiDPI.png)

#### Bluetooth | 蓝牙
![bluetooth](./imgs/iMac/bluetooth.png)

#### Airdrop | 隔空投送
![airdrop](./imgs/iMac/airdrop.png)

#### dGPU ｜ 独立显卡
![GPU](./imgs/iMac/gpu.png)

#### GPUs | 独立和集成显卡
![iGpu and dGPU](./imgs/iMac/igpu.png)

## 0. File index | 文件索引

| Dir / 目录               | Description / 描述                                                              | Type / 类型     |
| ----------------- | ------------------------------------------------------------------------- | --------- |
| `MacMini with iGPU/EFI`             | Supports macOS Monterey, Ventura & Sonoma(tested in Ventura)            | `Macmini 8,1 EFI`  |
| `iMac with dGPU/EFI`  | Supports macOS Monterey, Ventura & Sonoma(tested in Ventura)         | `iMac 18,3 EFI`  |

---

## 1. Hackintosh type | 设备类型

## 1.1 Macmini 8, 1

### Device Information | 设备信息
Macmini 2018, 8 gen core CPU with iGPU, without dGPU.
### Hardware | 硬件

|                     | Specifications / 型号               | Note / 备注 |
| ------------------- |:---------------------------------:|:---------:|
| Device/设备:     | ThinkCentre M910X                 |    |
| Motherboard/主板:     | Lenovo Q270                 |    |
| CPU/处理器:            | I5-7500T                          | Low-Power CPU   |
| iGPU/核显:            | HD630                          | Set display output   |
| Hard Drive/硬盘:      | WD SN730 512GB          |  M2 Nvme         | 
| RAM/内存:             | 8G DDR4 3200 * 2        |  16GB in total         |
| Wireless Card/无线网卡: | BCM94360cs2                   | Apple version from iMac     |
| Power/电源:           | 90W DC power adapter |  ThinkCentre power port         |

---

### Test | 测试
Pass. CPU and iGPU drive success.


## 1.2 iMac 18, 3
### Device Information | 设备信息
iMac 2017, 5K. 7 gen core desktop  CPU whit amd rx5x0 dGPU.
### Hardware | 硬件

|                     | Specifications / 型号               | Note / 备注 |
| ------------------- |:---------------------------------:|:---------:|
| Device/设备:     | ThinkCentre M910X                 |    |
| Motherboard/主板:     | Lenovo Q270                 |    |
| CPU/处理器:            | I5-7500T                          | Low-Power CPU   |
| iGPU/核显:            | HD630                          | Set compute only   |
| GPU/独立显卡:            | AMD RX460                          | same as RX560   |
| Hard Drive/硬盘:      | WD SN730 512GB          |  M2 Nvme         | 
| RAM/内存:             | 8G DDR4 3200 * 2        |  16GB in total         |
| Wireless Card/无线网卡: | BCM94360cs2                   | Apple version from iMac     |
| Power/电源:           | 90W DC power adapter |  ThinkCentre power port         |

---

### Information | 信息
* USB接口已定制，蓝牙内建，6个USB接口正常使用
* 无线网卡选取iMac拆机的bcm94360cs2网卡，macOS免驱，win有成熟驱动正常使用
* 核显设置为仅计算，独立显卡为RX460，与RX560为马甲关系，macOS免驱

### Test ｜ 测试
Pass.

## 2. Installation guideline | 安装指引
in dev.

## 3. Reference | 参考
in dev.
