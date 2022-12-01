
# 会话-设备（Device）

## 硬件信息

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| device.id | string | 设备唯一标识 | 1321321 | Required |
| device.brand | string | 设备品牌 | Meizu | Recommended |
| device.model | string | 设备型号 | m2 note | Recommended |
| device.ram | int | 设备整机RAM，单位:KB | 2000 | Recommended |
| device.rom | int | 设备整机ROM，单位:KB | 20000 | Recommended |
| device.vendor | string | 设备厂商 | mt6735 | Recommended |
| device.arch | string | 设备架构 | AArch64 Processor rev 4 (aarch64) | Recommended |

设备的所处区域运营商地理位置由数据上送服务自动识别。
## 系统信息

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| os.type | string | 设备系统类型 | android | Required |
| os.version | string | 设备系统版本 | 13.0 | Required |
| os.container | string | 设备容器名 | wechat、chrome、edge等 | Conditionally Required |
| os.container_version | string | 设备容器版本 | 1.0 | Conditionally Required |
