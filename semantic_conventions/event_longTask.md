
# 事件-卡顿（longTask）

## ANR,卡顿

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| longtask.view | string | 发生视图 | LoginActivity | Required |
| longtask.type | string | 卡顿类型 | | Recommended |
| longtask.source | string | 卡顿来源 | console,network | Required |
| longtask.caused_by | string | 卡顿原因 | "com.bonreesdk.hostdemo.business.lags.ComplexLogicActivity.resetArray(ComplexLogicActivity.java:28)" | Required |
| longtask.call_stacks | array | 应用卡顿调用栈 | 详见[应用异常调用栈（CallStack）](./event_exception.md#应用异常调用栈callstack)定义 | Required |
| longtask.binary_images | array | 应用二进制文件信息 | 详见[二进制文件信息（BinaryImage）](./event_exception.md#二进制文件信息binaryimage)定义 | Conditionally Required |
| longtask.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common_scene.md) | Required |
