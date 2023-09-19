# Thinkcentre-M910X-Hackintosh-OC-EFI
## OpenCore version 0.9.5

images and install guid will be uploaded after all testing is complete.

## 0. File index | 文件索引

|    Dir / 目录                 | Note / 备注               | 
| ------------------- |:---------------------------------:|
| MacMini with iGPU     |    Macmini 8,1 EFI   |    
| iMac with dGPU     | iMac 18,3 EFI                 |    



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
in dev.
