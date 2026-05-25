# 无人机

## 硬件

### 主板图示



### 硬件详细信息

|    类型    |   制造商   |      型号       |         规格         |                         手册或详情页                         |
| :--------: | :--------: | :-------------: | :------------------: | :----------------------------------------------------------: |
|   处理器   | HiSilicon  |   Hi3519DV500   | 2 × 1Ghz Cortex-A55  | [详情页](https://www.hisilicon.com/cn/products/smart-vision/machine-vision/hi3519dv500) |
| 图像传感器 |    SONY    |     IMX582      |      1/2" 48MP       |                                                              |
|    飞控    | GigaDevice |    GD32F470     |   240Mhz Cortex-M4   | [详情页](https://www.gigadevice.com/product/mcu/high-performance-mcus/gd32f4xx-series/gd32f470) |
|    图传    |  Artosyn   |    AR8032S2     | XuanTie E907 RV32IMA | [Artosyn 产品页](http://www.artosyn.cn/official_product/list/9/11.html), [XuanTie E907 详情页](https://www.xrvm.cn/product/xuantie/E907) |
|  射频前端  | Kxcomtech  |    KCT8285HE    |      2.4Ghz FEM      |    [详情页](https://www.kxcomtech.com/product/info/1064)     |
| 云台控制器 |    XHSC    |    HC32F460     |   200Mhz Cortex-M4   |     [详情页](https://www.xhsc.com.cn/product/1246.html)      |
|    电调    |   LKSMCU   |      LKS07      |   96MHz Cortex-M0    |   [详情页](https://www.lksmcu.com/index.php/LKS07Series/)    |
|    无线    |  Realtek   |    RTL8821CS    |   WiFI 5 + BT 4.2    | [产品页](https://www.realtek.com/Product/Index?id=588&cate_id=194) |
|    RAM     |  Samsung   | K4A8G165WC-BCTD |     DDR4 2 × 1GB     |                                                              |
|    ROM     |    MXIC    |  MX35UF4GE4AD   |        512MB         | [详情页](https://www.mxic.com.tw/zh-tw/products/NAND-Flash/Serial-NAND-Flash/Pages/spec.aspx?p=MX35UF4GE4AD&m=Serial%20NAND&n=PM2967) |

1. 在以上列表之 "手册或详情页" 部分中
	1. "详情页" 表示页面具有这个产品的 DataSheet、UserManual 等全面的资料
	2. "产品页" 表示页面具有这个产品的部分规格信息，但没有较为详尽的资料
	3. 留空表示没有找到这个制造商官网的资料，但仍可能存在第三方资料

---

## 软件

除了嵌入式部分，Potensic ATOM 2 在 HiSilicon Hi3519DV500 上运行着一个 GNU/Linux 操作系统，版本是 5.10.0，与 HiSilicon Hi3519DV500 详情页上宣称提供的 Linux SDK 版本相符

这一部分主要用于与相机、RC、客户端通信，在内部被称作 CAM

### 升级包

Potensic 使用一个自定义的软件升级包体，后缀是 .bin。由 4 字节的头部 Magic，以 JSON 存储的 Metadata，经过 AES-CBC 加密的数个 Chunk 组成

无人机和遥控器部分使用相同形式的升级包体，但 AES-CBC 的 Key 不同

Metadata 部分的格式如下所示，提取自 25.01 版本的无人机端升级包

```json
{
    "modules": [
        {
            "dev_id": [
                112
            ],
            "md5": "0ec28f7abf01f2c4aadccc74d1213349",
            "name": "bms_device_bt02a_v1.5.5_20250403.bin",
            "padded_size": 24240,
            "prio": 10,
            "product_type": "atom2",
            "size": 24228,
            "type": "bms",
            "version": "1.5.5"
        },
        {
            "dev_id": [
                113
            ],
            "md5": "78c5cda374180a149178cc9248dc647e",
            "name": "bms_device_bt02b_v1.3.4_20250403.bin",
            "padded_size": 23936,
            "prio": 11,
            "product_type": "atom2",
            "size": 23932,
            "type": "bms",
            "version": "1.3.4"
        },
        {
            "dev_id": [
                114
            ],
            "md5": "8a23a0ec1f8cb797a6137b4c761f7f5e",
            "name": "bms_device_bt02c_v2.0.6_20250403.bin",
            "padded_size": 35376,
            "prio": 12,
            "product_type": "atom2",
            "size": 35368,
            "type": "bms",
            "version": "2.0.6"
        },
        {
            "dev_id": [
                115
            ],
            "md5": "643915d322865709cde74f7a1a10bdc6",
            "name": "bms_device_bt02d_v3.1.0_20250918.bin",
            "padded_size": 34976,
            "prio": 13,
            "product_type": "atom2",
            "size": 34968,
            "type": "bms",
            "version": "3.1.0"
        },
        {
            "dev_id": [
                116
            ],
            "md5": "d27743098847790eba1675f5158d82b8",
            "name": "bms_device_bt02e_v4.0.6_20250902.bin",
            "padded_size": 36064,
            "prio": 14,
            "product_type": "atom2",
            "size": 36056,
            "type": "bms",
            "version": "4.0.6"
        },
        {
            "dev_id": [
                117
            ],
            "md5": "35d63b5641303bcd68ef8786b0fce116",
            "name": "bms_device_bt02f_v5.0.6_20250403.bin",
            "padded_size": 24512,
            "prio": 15,
            "product_type": "atom2",
            "size": 24508,
            "type": "bms",
            "version": "5.0.6"
        },
        {
            "dev_id": [
                118
            ],
            "md5": "d558dbdf2f2cadbcc025d925daf00485",
            "name": "bms_device_bt02g_v6.0.4_20250902.bin",
            "padded_size": 36064,
            "prio": 16,
            "product_type": "atom2",
            "size": 36060,
            "type": "bms",
            "version": "6.0.4"
        },
        {
            "dev_id": [
                133
            ],
            "md5": "b03dd0ece8dda5cee59821f2c81b62d1",
            "name": "gimbal_atom2_bs_v2.6.9_20260403.bin",
            "padded_size": 104192,
            "prio": 20,
            "product_type": "atom2",
            "size": 104184,
            "type": "gimbal",
            "version": "2.6.9"
        },
        {
            "dev_id": [
                131
            ],
            "md5": "0363872252a3e7df3aa569c025f7449e",
            "name": "gimbal_atom2_updata_v2.3.2_20260403.bin",
            "padded_size": 104176,
            "prio": 22,
            "product_type": "atom2",
            "size": 104164,
            "type": "gimbal",
            "version": "2.3.2"
        },
        {
            "dev_id": [
                179,
                185,
                186,
                187
            ],
            "md5": "945214437c25172f75798d3146b179a1",
            "name": "fcs_atom2_gd32f470vg_v4.8.12_20260413.bin",
            "padded_size": 727632,
            "prio": 30,
            "product_type": "atom2",
            "size": 727628,
            "type": "fcs",
            "version": "4.8.12"
        },
        {
            "dev_id": [
                36,
                37,
                38,
                39
            ],
            "md5": "ad81f450a9d78e66ca5a3f9b02f81d59",
            "name": "esc_device_lk074_v2.0.10_20260327.bin",
            "padded_size": 24560,
            "prio": 41,
            "product_type": "atom2",
            "size": 24552,
            "type": "esc",
            "version": "2.0.10"
        },
        {
            "dev_id": [
                6
            ],
            "md5": "0d2bcc736ee2304232ba1e8263627230",
            "name": "cam_atom2_v8.12.24_20260420.appsw",
            "padded_size": 81279920,
            "prio": 50,
            "product_type": "atom2",
            "size": 81279907,
            "type": "cam",
            "version": "8.12.24"
        }
    ],
    "product_type": "atom2",
    "version": "025.01"
}
```

除了 MCU 所用的固件，CAM 部分使用一个 UBIFS 的镜像包，包含 Linux RootFS，后缀是 .appsw

大量用户在 Reddit 反馈它们的 Potensic ATOM 2 在升级到 24.02 版本后出现了包括但不限于相机失焦、成像模糊等问题。但有趣的是，24.02 版本固件相对于上一个版本 23.03 只更新了飞控固件，并没有任何能够影响到相机的更改

### 分区

Potensic ATOM 2 具有 512 MB 的 ROM，其分区映射如下所示。部分分区具有备份分区，备份分区的分区名以下划线开头

| 编号 |    分区名     | 挂载点 | 大小 (KB) |
| :--: | :-----------: | :----: | :-------: |
|  1   |  boot_image   |  mtd0  |   1024    |
|  2   |     bl31      |  mtd1  |   1024    |
|  3   |   rawparam    |  mtd2  |   1024    |
|  4   |  rawparambak  |  mtd3  |   1024    |
|  5   |   resImage    |  mtd4  |   1024    |
|  6   |    uImage     |  mtd5  |   15360   |
|  7   | rootfs.ubifs  |  mtd6  |   32768   |
|  8   |  appfs.ubifs  |  mtd7  |   98304   |
|  9   |   _rawparam   |  mtd8  |   1024    |
|  10  | _rawparambak  |  mtd9  |   1024    |
|  11  |   _resImage   | mtd10  |   1024    |
|  12  |    _uImage    | mtd11  |   15360   |
|  13  | _rootfs.ubifs | mtd12  |   32768   |
|  14  | _appfs.ubifs  | mtd13  |   98304   |
|  15  |   data.bin    | mtd14  |  223232   |
