# 无人机

## 硬件

### 硬件详细信息

|    类型    |   制造商   |    型号     |         规格         |                         手册或详情页                         |
| :--------: | :--------: | :---------: | :------------------: | :----------------------------------------------------------: |
|   处理器   | HiSilicon  | Hi3519DV500 | 2 × 1Ghz Cortex-A55  | [详情页](https://www.hisilicon.com/cn/products/smart-vision/machine-vision/hi3519dv500) |
| 图像传感器 | OmniVision |    OV50H    |     1/1.3" 50MP      |                                                              |
|    飞控    | GigaDevice |  GD32F470   |   240Mhz Cortex-M4   | [详情页](https://www.gigadevice.com/product/mcu/high-performance-mcus/gd32f4xx-series/gd32f470) |
|    图传    |  Artosyn   |  AR8032S2   | XuanTie E907 RV32IMA | [Artosyn 产品页](http://www.artosyn.cn/official_product/list/9/11.html), [XuanTie E907 详情页](https://www.xrvm.cn/product/xuantie/E907) |
|  射频前端  |            |             |                      |                                                              |
| 云台控制器 |  ARTERY ?  |   AT32 ?    |                      |                                                              |
|    电调    |   LKSMCU   |    LKS07    |   96MHz Cortex-M0    |   [详情页](https://www.lksmcu.com/index.php/LKS07Series/)    |
|    无线    |            |             |                      |                                                              |
|    RAM     |            |             |                      |                                                              |
|    ROM     |            |             |                      |                                                              |

1. 在以上列表之 "手册或详情页" 部分中
  1. "详情页" 表示页面具有这个产品的 DataSheet、UserManual 等全面的资料
  2. "产品页" 表示页面具有这个产品的部分规格信息，但没有较为详尽的资料
  3. 留空表示没有找到这个制造商官网的资料，但仍可能存在第三方资料
2. Potensic ATOM 3 的大部分硬件都与 Potensic ATOM 2 相同，部分缺少型号的条目是因为暂时缺少主板图片而无法识别
3. 能够通过部分特征识别可能的品牌、系列、型号，但无法确定的，使用 "?" 标记

---

### 升级包

Potensic 使用一个自定义的软件升级包体，后缀是 .bin。由 4 字节的头部 Magic，以 JSON 存储的 Metadata，经过 AES-CBC 加密的数个 Chunk 组成

无人机和遥控器部分使用相同形式的升级包体，但 AES-CBC 的 Key 不同

Metadata 部分的格式如下所示，提取自 12.02 版本的无人机端升级包

```json
{
    "modules": [
        {
            "dev_id": [
                119
            ],
            "md5": "4943aac4288bb9b9d63bc8d921c8bc1d",
            "name": "bms_device_bt02h_v7.1.5_20260415.bin",
            "padded_size": 36352,
            "prio": 17,
            "product_type": "atom3",
            "size": 36352,
            "type": "bms",
            "version": "7.1.5"
        },
        {
            "dev_id": [
                120
            ],
            "md5": "5e95fce34b61dc6edb5464894fedeb53",
            "name": "bms_device_bt02i_v8.0.9_20260210.bin",
            "padded_size": 35744,
            "prio": 18,
            "product_type": "atom3",
            "size": 35744,
            "type": "bms",
            "version": "8.0.9"
        },
        {
            "dev_id": [
                134
            ],
            "md5": "cf8fda995544967d0f278837708168e4",
            "name": "gimbal_atom3_updata_v3.2.5_20260509.bin",
            "padded_size": 84544,
            "prio": 23,
            "product_type": "atom3",
            "size": 84532,
            "type": "gimbal",
            "version": "3.2.5"
        },
        {
            "dev_id": [
                181
            ],
            "md5": "f6213abc67fcce04fcf928a2dec17790",
            "name": "fcs_atom3_gd32f470vg_v5.3.2_20260515.bin",
            "padded_size": 794560,
            "prio": 30,
            "product_type": "atom3",
            "size": 794556,
            "type": "fcs",
            "version": "5.3.2"
        },
        {
            "dev_id": [
                36,
                37,
                38,
                39
            ],
            "md5": "8234b12181c69e0e15614494a59e1608",
            "name": "esc_device_lk074_v4.0.8_20260113.bin",
            "padded_size": 24944,
            "prio": 41,
            "product_type": "atom3",
            "size": 24944,
            "type": "esc",
            "version": "4.0.8"
        },
        {
            "dev_id": [
                9
            ],
            "md5": "0621d88f58177bc62ec3bd80b794ffea",
            "name": "cam_atom3_v7.5.24_20260515.appsw",
            "padded_size": 78004640,
            "prio": 50,
            "product_type": "atom3",
            "size": 78004636,
            "type": "cam",
            "version": "7.5.24"
        }
    ],
    "product_type": "atom3",
    "version": "012.02"
}
```

除了 MCU 所用的固件，CAM 部分使用一个 UBIFS 的镜像包，包含 Linux RootFS，后缀是 .appsw

