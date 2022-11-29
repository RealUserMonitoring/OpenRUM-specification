
# 事件-网络请求（Resource）

| Attribute | Type | Description | Examples | Requirement Level |
| -- | -- | -- | -- | -- |
| resource.url | string | HTTP请求完整URL<br>scheme://host[:port]/path?query[#fragment] [1] | https://www.bonree.com | Required |
| resource.method | string | HTTP请求方法 | GET;POST | Required |
| resource.host | string | HTTP Header中的host [2] | www.bonree.com | Recommended |
| resource.scheme | string | URL协议的scheme标识 | http;https;tcp; | Recommended |
| resource.status_code | int | [HTTP response status code](https://tools.ietf.org/html/rfc7231#section-6) | 200 | Conditionally Required |
| resource.view_id | string |视图id | 6F9619FF-8B86-D011-B42D-00C04FC964FF | Required |
| resource.trace_id | string | 资源请求 traceId | 6F9619FF-8B86-D011-B42D-00C04FC964FF | Recommended |
| resource.flavor | string | HTTP 协议类型 [3] | 1.1 | Recommended |
| resource.client.tcp.ip | string | 接收方远程IP地址（IPv4使用十进制点分格式，IPv6参考[RFC5952](https://tools.ietf.org/html/rfc5952)） | 127.0.0.1 | Recommended |
| resource.client.tcp.port | int | 远程端口号 | 80;8080;443 | Recommended |
| resource.request.content_length | int | 请求数据的字节大小，包括请求头的传输字节大小，可能与请求头内的Content-Length有差异。 | 1024 | Recommended |
| resource.request.header.<key> | string[] | HTTP请求头，<key>是HTTP请求头字段名（小写，"-"符替换为"_"），值是请求头字段对应值。[4] | http.request.header.content_type=["application/json"]; | Recommended |
| resource.response.content_length | int | 响应数据的字节大小，包括响应头的传输字节大小，可能与响应头内的Content-Length有差异。 | 2048 | Recommended |
| resource.response.header.<key> | string[] | HTTP响应头，<key>是HTTP响应头字段名（小写，"-"符替换为"_"），值是响应头字段对应值。[4] | http.response.header.content_type=["application/json"]; | Recommended |
| resource.timing_data | object | 性能指标 | 详见[性能指标（TimingData）](#http请求性能指标timingdata)定义 | Required |
| resource.error_msg | string | 错误信息[5] | The host name for a URL couldn’t be resolved. | Recommended |
| resource.scene.(现场属性) | object | 事件发生时的设备状态信息 | 详见[现场属性](./event_common_scene.md) | Required |

[1]：URL中不要携带鉴权信息。如请求为https://username:password@www.bornee.com/，request.url属性应设置https://www.bonree.com/。

[2]：resource.host属性应与请求头的host字段保持一致，如果请求头中host字段无赋值，request.host属性也不要赋值。

[3]：resource.flavor有如下表定义。如表内定义适用，务必参照表内定义使用。其它情况可以使用自定义的值。

| Type | Description |
| -- | -- |
| 1.0 | HTTP/1.0 |
| 1.1 | HTTP/1.1 |
| 2.0 | HTTP/2 |
| 3.0 | HTTP/3 |
| SPDY | SPDY协议 |
| QUIC | QUIC协议 |

[4]：对于获取的标头信息需要明确配置。获取全部的请求头或响应头可能存在安全风险，显式配置需要的字段可避免敏感信息的泄露。部分头字段如Host已经在属性中明确定义，在请求头或响应头中也可以额外配置。

[5]：错误信息一旦设置，网络请求会被认为是错误请求。可以设置框架抛出或自定义网络请求的错误信息。

## Http请求性能指标（TimingData）

指标定义参考[W3C规范](https://www.w3.org/TR/navigation-timing/#performancetiming)。

| Attribute | Type | Requirement Level |
| -- | -- | -- |
| navigation_start | int | Recommended |
| unload_event_start | int | Recommended |
| unload_event_end | int | Recommended |
| redirect_start | int | Recommended |
| redirect_end | int | Recommended |
| fetch_start | int | Recommended |
| domain_lookup_start | int | Required |
| domain_lookup_end | int | Required |
| connect_start | int | Required |
| connect_end | int | Required |
| secure_connection_start | int | Required |
| request_start | int | Required |
| response_start | int | Required |
| response_end | int | Required |
| dom_loading | int | Recommended |
| dom_interactive | int | Recommended |
| dom_content_loaded_event_start | int | Recommended |
| dom_content_loaded_event_end | int | Recommended |
| dom_complete | int | Recommended |
| load_event_start | int | Recommended |
| load_event_end | int | Recommended |
