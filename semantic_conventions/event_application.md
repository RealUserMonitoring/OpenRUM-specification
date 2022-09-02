
# 事件-应用行为（application）

## 应用公共属性

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| app.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common.md) | Required |

## 应用启动

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| app.launch.type | int | 启动类型，0:unknown未知类型; 1:冷启动; 2:热启动; 3:首次启动 [1] | 1;2;3; | Required |
| app.launch.load_time | int | 启动加载耗时，单位:ms [2] | 200 | Required |
| app.launch.snapshot | object[] | 应用启动线程方法快照，线程方法对象数组 [3] | 详见[线程方法快照（Snapshot）](./event_user_action.md#线程方法快照snapshot) | Recommended |

## 应用退出

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| app.exit.duration | int | 应用运行持续时间，单位:ms [4] | 100000 | Required |

## 应用前后台切换

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| app.background.load_time | int | 应用退后台耗时，单位:ms [5] | 200 | Required |
| app.forground.load_time | int | 应用进入前台耗时，单位:ms [5] | 200 | Required |
| app.forground.bg_duration | int | 应用进入前台前在后台的停留时长，单位:ms | 60000 | Recommended |

[1]：应用的启动，分为冷启动、热启动、首次启动三种类型。冷启动指应用进程从内存加载到完全启动的完整过程；热启动指应用进程已在内存中存在，从后台挂起的状态到重新回到前台运行的过程；首次启动是特殊的冷启动，指应用或应用的最新版本首次在当前设备上运行的冷启动过程。type字段的取值必须在以下定义中设置，否则均识别为未知启动类型。

| Value | Description |
| -- | -- |
| 1 | 冷启动 |
| 2 | 热启动 |
| 3 | 首次启动 |

[2]：应用加载耗时推荐统计应用从内存中加载或从后台调起时开始，到首个视图展示结束的完整时间。

[3]：应用启动线程方法快照可记录启动过程中的关键方法执行所在的线程以及方法名称、执行耗时等信息，如应用、视图生命周期，数据IO接口，数据解析方法等。

[4]：应用运行持续事件可记录上次冷/热启动到退出的持续时间。

[5]：退后台与进入前台的耗时表示从操作开始到完成退后台/进前台切换的耗时，可以衡量切换过程中各种现场保存、状态记录、数据初始化等操作的性能。
