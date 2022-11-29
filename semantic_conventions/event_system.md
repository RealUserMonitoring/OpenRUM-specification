
# 事件-系统（System）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| sys.net_change.before.ip | string | 网络切换前的外部IP（IPv4使用十进制点分格式，IPv6参考RFC5952） | 1.1.1.1 | Conditionally Required |
| sys.net_change.before.standard | string | 网络切换前的网络制式 [1] | wifi;LTE | Required |
| sys.net_change.after.ip | string | 网络切换后的外部IP（IPv4使用十进制点分格式，IPv6参考RFC5952） | 2.2.2.2 | Conditionally Required |
| sys.net_change.after.standard | string | 网络切换后的网络制式 [1] | NR | Required |
| sys.model_change | string | 运行模式切换 | power save mode | Required |
| sys.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common_scene.md) | Required |
