
# 事件-应用异常（exception）

## 应用崩溃（Crash）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| crash.id | string | 应用崩溃唯一标识 | 123123 | Required |
| crash.type | string | 应用崩溃类型 | RangeError | Required |
| crash.caused_by | string | 应用崩溃原因 | Invalid array length | Required |
| crash.view | string | 发生视图 | LoginActivity | Required |
| crash.thread.id | string | 应用崩溃线程ID [1] | 1234 | Required |
| crash.call_stacks | object[] | 应用崩溃调用栈 [1] | 详见[应用异常调用栈（CallStack）](#应用异常调用栈callstack)定义 | Required |
| crash.binary_images | object[] | 应用二进制文件信息 [2] | 详见[二进制文件信息（BinaryImage）](#二进制文件信息binaryimage)定义 | Conditionally Required |
| crash.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common.md) | Required |

[1]：崩溃调用栈的信息以线程的维度拆分，记录每个线程内的堆栈，崩溃线程ID应于发生崩溃的线程堆栈的call_stack对象中的thread.id保持一致。

[2]：iOS系统下发生的崩溃会使用到二进制文件信息，用于崩溃符号解析。

## JS错误（JSError）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| js_error.type | string | 应用崩溃类型 | RangeError | Required |
| js_error.caused_by | string | 应用崩溃原因 | Invalid array length | Required |
| js_error.call_stack | object | 应用崩溃调用栈 [1] | 详见[应用异常调用栈（CallStack）](#应用异常调用栈callstack)定义 | Required |
| js_error.view | string | 发生页面 | http://www.bonree.com | Required |
| js_error.file | string | 发生错误的JS文件 [2] | test.js | Required |
| js_error.line | int | JS错误行号 | 100 | Required |
| js_error.column | int | JS错误列号 | 10 | Required |
| js_error.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_scene.md) | Required |

[1]：JS错误的堆栈通畅不涉及线程，不需要使用数组接口记录多个线程，使用对象记录堆栈即可。

[2]：文件路径使用绝对路径、相对路径、资源URL均可。

## ANR

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| anr.type | string | ANR类型 | | Recommended |
| anr.caused_by | string | ANR原因 | "com.bonreesdk.hostdemo.business.lags.ComplexLogicActivity.resetArray(ComplexLogicActivity.java:28)" | Required |
| anr.view | string | 发生视图 | LoginActivity | Required |
| anr.call_stack | object | ANR主线程调用栈 | 详见[应用异常调用栈（CallStack）](#应用异常调用栈callstack)定义 | Required |
| anr.trace | string | ANR内存现场 | | Required |
| anr.message | string | ANR内存环境信息 | | Recommended |
| anr.class | string | 发生ANR的类 | ComplexLogicActivity | Required |
| anr.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_scene.md) | Required |

## 应用卡顿（Lag）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| lag.view | string | 发生卡顿的视图名称 | LoginActivity | Recommended |
| lag.call_stacks | array | 应用卡顿调用栈 | 详见[应用异常调用栈（CallStack）](#应用异常调用栈callstack)定义 | Required |
| lag.binary_images | array | 应用二进制文件信息 | 详见[二进制文件信息（BinaryImage）](#二进制文件信息binaryimage)定义 | Conditionally Required |
| lag.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_scene.md) | Required |

## 应用异常调用栈（CallStack）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| call_stack.thread.id | string | 调用线程ID | 1234 | Required |
| call_stack.thread.name | string | 调用线程名称 | thread-main | Recommended |
| call_stack.info | string | 堆栈信息 [1] | | Required |

[1]：异常堆栈信息中多行调用栈使用换行符\n拼接为字符串即可。

## 二进制文件信息（BinaryImage）

参考[Apple官方文档](https://developer.apple.com/documentation/xcode/examining-the-fields-in-a-crash-report)关于Binary Image的定义。

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| binary_image.name | string | 二进制文件名称 | Foundation | Required |
| binary_image.uuid | string | 二进制文件的UUID | 7482ad1b76ee38b48dac0960f9f9521e | Required |
| binary_image.arch | string | 文件架构 | arm64 | Required |
| binary_image.base_addr | string | 基址 | 0x181d84000 | Required |
| binary_image.path | string | 文件路径 | /System/Library/Frameworks/Foundation.framework/Foundation | Required |
