# 充电盒

## 硬件

| 类型 |        制造商         |   型号    |    规格     |                         手册或详情页                         |
| :--: | :-------------------: | :-------: | :---------: | :----------------------------------------------------------: |
| MCU  |       Allwinner       |  F133-A   | RISC-V 1Ghz | [详情页](https://www.allwinnertech.com/index.php?c=product&a=index&id=101) |
| 蓝牙 |       IngChips        | ING91870C |             | [详情页](https://www.semiee.com/3143735c-b1cb-4087-8cb7-d410e16b6230.html) |
| PMIC | Halo Microelectronics |  HL7019   |             | [详情页](https://www.halomicro.cn/pro_detail/998965472187371520.html) |

---

## 软件

充电盒内部使用 Melis RTOS 操作系统

充电盒在 USB 上开放 ADB 调试，当相机处于关闭状态时，将充电盒连接到电脑，则会出现 ADB 设备，默认 Shell 是 RTOS 的 msh

ADB 通过 Gadget 形式提供

---

## 通信

因为充电盒和相机本体可以分离工作，充电盒和相机之间有如下通信方式

- 当充电盒和相机通过触点连接时，两者经由 USB 通信

- 当充电盒和相机分离时，两者经由 2.4Ghz 蓝牙通信

	蓝牙芯片 ING91870C 则通过 SPI + DMA 与 F133-A 通信

