
# 事件-自定义（custom）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| custom.event.id | string | 自定义事件唯一标识 | 123123 | Required |
| custom.event.name | string | 自定义事件名称 | 加入购物车 | Recommended |
| custom.event.duration | int | 自定义事件耗时，单位:ms | 200 | Recommended |
| custom.event.<key> | string | 自定义事件附加信息，<key>可以使用任意字母、数字、下划线组成的字段，value可以设置任意字符串信息。最大限制100条数据。 | custom.event.count="100";<br>custom.event.user_name="张三"; | Recommended |
| custom.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_scene.md) | Required |
