
# 会话-设备（device）

## Common Attributes

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| device.id | string | 设备唯一标识 | 1321321 | Required |
| device.hardware.brand | string | 设备品牌 | Meizu | Recommended |
| device.hardware.model | string | 设备型号 | m2 note | Recommended |
| device.hardware.ram | int | 设备整机RAM，单位:KB | 2000 | Recommended |
| device.hardware.rom | int | 设备整机ROM，单位:KB | 20000 | Recommended |
| device.hardware.vendor | string | 设备厂商 | mt6735 | Recommended |
| device.hardware.arch | string | 设备架构 | AArch64 Processor rev 4 (aarch64) | Recommended |
| device.os.type | string | 设备系统类型 | android | Required |
| device.os.version | string | 设备系统版本 | 13.0 | Required |
| device.os.build | string | 设备系统build版本 | 19G82 | Conditionally Required |
| device.os.container | string | 设备容器名 | wechat | Conditionally Required |
| device.os.container_version | string | 设备容器版本 | 1.0 | Conditionally Required |

设备的所处区域运营商地理位置由数据上送服务自动识别。
