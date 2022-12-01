
# 事件-用户操作（UserAction）

## 用户操作公共属性

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| action.id | string | 用户操作唯一标识 [1] | 123123 | Required |
| action.type | string | 操作类型  | 0:其他 1:点击,2:手势，3:键盘，4:输入 | Required |
| action.name | string | 用户操作控件名称 [2] | 登录 | Required |
| action.method_info | string | 用户操作方法信息 | onClick() | Required |
| action.view | string | 操作控件所在视图  | LoginActivity | Required |
| action.duration | int | 操作耗时，单位:ms [3] | 200 | Required |
| action.snapshots | object[] | 操作线程方法快照，线程方法对象数组 [4] | 详见[线程方法快照（Snapshot）](#线程方法快照snapshot) | Recommended |
| action.scene | object | 事件发生时的设备状态信息 | 详见[现场属性](./common_scene.md) | Required |

[1]：标识每次操作的唯一标识，可以任意设置，要求每次操作必须唯一，即使相同控件的多次操作也应设置不同的ID。

[2]：操作控件名称推荐使用控件的标题或者类名，对于敏感信息如自定义的密码输入按钮、验证码输入框等控件应做脱敏处理。

[3]：操作耗时推荐使用点击操作的响应方法的执行耗时，也可结合业务相关流程，以关键业务节点作为操作的耗时。

[4]：操作线程方法快照可以记录操作耗时表示的过程中的关键方法执行所在的线程以及方法名称、执行耗时等信息，如视图生命周期，数据IO接口，数据解析方法等。

## 线程方法快照（Snapshot）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| snapshot.thread.id | string | 线程唯一标识 | 123 | Required |
| snapshot.thread.name | string | 线程名称 | thread-123 | Recommended |
| snapshot.thread.is_main | bool | 当前线程是否是主线程 | true;false | Required |
| snapshot.methods | object[] | 当前线程内执行的方法信息，方法信息对象数组 | 详见[方法信息（Method）](#方法信息method) | Required |

## 方法信息（Method）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| method.name | string | 方法名称 | 123123 | Required |
| method.start_time | int | 方法执行开始时间戳，单位:ms | 1660199506723 | Required |
| method.end_time | int | 方法执行结束时间戳，单位:ms | 1660199506923 | Required |
