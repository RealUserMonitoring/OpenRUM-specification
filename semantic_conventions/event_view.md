
# 事件-视图（View）

## 视图公共属性

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| view.id | string | 视图唯一标识 [1] | 123123 | Required |
| view.name | string | 视图名称 [2] | LoginActivity | Recommended |
| view.url | string | 页面URL [3] | https://www.bonree.com | Conditionally Required |
| view.type | int | 视图类型 [4] | 1;2;3; | Required |
| view.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common_scene.md) | Required |

## 视图加载

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| view.load.time | int | 视图加载耗时，单位:ms [5] | 200 | Required |
| view.largest_contentful_paint | int | 页面加载时间线中呈现视口中最大 DOM 对象（屏幕上可见）的时刻 | 2.5 | Recommended |
| view.first_input_delay | int | 从用户第一次与页面交互到浏览器响应之间经过的时间。 | 100 | Recommended |
| view.cumulative_layout_shift | int | 量化由于动态加载的内容（例如，第三方广告）而导致的意外页面移动，其中 0 表示没有发生变化。 | 0.1 | Recommended |
| view.load.snapshots | object[] | 视图加载线程方法快照，线程方法对象数组 | 详见[线程方法快照（Snapshot）](./event_user_action.md#线程方法快照snapshot) [6] | Conditionally Required |
| view.load.timing_data | object | 页面主文档加载性能 | 详见[性能指标（TimingData）](./event_resource.md#http请求性能指标timingdata)定义 [7] | Conditionally Required |

## 视图退出

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| view.exit.duration | int | 视图停留时长，单位:ms | 10000 | Required |


[1]：标识每次视图加载的唯一标识，可以任意设置，但是要求每次加载必须唯一，即使相同页面的多次加载也应设置不同的ID。

[2]：视图名称推荐使用视图类名或标题，对于H5页面可以使用URL或Title。

[3]：页面URL中不要携带鉴权信息。如请求为https://username:password@www.bornee.com/，应设置为https://www.bonree.com/。当视图类型为web页面时，view.url属性为必填。

[4]：视图类型标识采集的视图类型归属于哪类框架。只能使用如下定义，否则会识别为未知视图。

| Value | Description |
| -- | -- |
| 1 | Native原生视图 |
| 2 | Web页面 |
| 3 | ReactNative页面 |
| 4 | Flutter页面 |
| 5 | 小程序页面 |

[5]：视图加载耗时推荐使用视图加载到完成展示的完整时间。

[6]：视图加载线程方法快照可记录加载过程中的关键方法执行所在的线程以及方法名称、执行耗时等信息，如视图生命周期，数据IO接口，数据解析方法等。

[7]：当视图类型为web页面时，需按照[W3C规范](https://www.w3.org/TR/navigation-timing/#performancetiming)定义记录页面的性能指标。

[8]：当视图类型为web页面时，记录页面内元素的加载性能。指标可参考[W3C规范](https://www.w3.org/TR/navigation-timing/#performancetiming)。

