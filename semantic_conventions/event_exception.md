
# 事件-应用异常（Exception）

## 应用崩溃（Crash）、JS错误（JSError）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| exception.id | string | 应用崩溃唯一标识 | 123123 | Required |
| exception.type | string | 应用崩溃类型 | RangeError | Required |
| exception.source | string | 错误来源 | console,network | Required |
| exception.caused_by | string | 应用崩溃原因 | Invalid array length | Required |
| exception.view | string | 发生视图 | LoginActivity | Required |
| exception.thread.id | string | 应用崩溃线程ID [1] | 1234 | Required |
| exception.call_stacks | array | 应用崩溃调用栈 [1] | 详见[应用异常调用栈（CallStack）](#应用异常调用栈callstack)定义 | Required |
| exception.binary_images | array | 应用二进制文件信息 [2] | 详见[二进制文件信息（BinaryImage）](#二进制文件信息binaryimage)定义 | Conditionally Required |
| exception.scene | object | 事件发生时的设备状态信息 | 详见[现场属性](./common_scene.md) | Required |
| exception.file | string | 发生错误的文件 [2] | test.js | Required |
| exception.line | int | 错误行号 | 100 | Required |
| exception.column | int | 错误列号 | 10 | Required |

[1]：崩溃调用栈的信息以线程的维度拆分，记录每个线程内的堆栈，崩溃线程ID应于发生崩溃的线程堆栈的call_stack对象中的thread.id保持一致。

[2]：iOS系统下发生的崩溃会使用到二进制文件信息，用于崩溃符号解析。

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
