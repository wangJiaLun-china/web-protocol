[TOC]

# 网络协议(常用web相关)

- **应用层**

  - HTTP/1.1(Hypertext Transfer Protocol)

    - (RFC7230 2014.6)一种无状态的,应用层的,以请求/应答方式运行的协议,使用可扩展

      的语义和自描述消息格式,与基于网络的超文本信息系统灵活互动

  - Websocket

  - HTTP/2.0

- 应用层中安全基础设施

  - TLS/SSL

- 传输层

  - TCP

- 网络层及数据链路层

  - IP 和 以太网

## HTTP/1

- 缺陷: 不支持服务器端主动的推送消息


- 浏览器发起HTTP请求的步骤

  ```mermaid
  graph TD
  A[用户界面] --> B["浏览器引擎(查询和操作渲染引擎)"]
  B["浏览器引擎(查询和操作渲染引擎)"]--> C[渲染引擎]
  B["浏览器引擎(查询和操作渲染引擎)"]--> G["数据存储(浏览器的轻量数据库)"]
  C["渲染引擎(解析,渲染请求内容)"] --> D[网络]
  C["渲染引擎(解析,渲染请求内容)"] --> E["JS解释器(解析执行JS)"]
  C["渲染引擎(解析,渲染请求内容)"] -->  F["UI后端(负责绘制)"]
  A[用户界面] --> F["UI后端(负责绘制)"]
  ```

  ​

- HTTP 协议格式(基于ABNF语义)

  start-line(请求和响应的第一行)

  - request-line(请求行) : GET /HTTP/1.1*
  - status-line(响应行) : HTTP/1.1 200 OK

  header-field

  - Date
  - Host
  - Content-Type
  - Connection

  message-body

- ABNF(扩充巴科斯-瑙尔范式)操作符

  - 空白字符: 用来分割定义中的各个元素(实际空格使用 SP 代替)

    - method SP request-target SP HTTP-version CRLF

  - 选择 /: 表示多个规则都是可供选择的规则

    - start-line = request-line / status-line

  - 值范围 %c##-## :

    - OCTAL = "0" / "1" / "2" / "3" / "4" / "5" / "6" / "7" 等价于

      OCTAL = %x30-37

  - 序列组合(): 将规则组合起来,视为单个元素

  - 不定量重复 m*n:

    - 元素表示零个或更多元素: *( header-field CRLF)
    - 1* 表示一个活更多元素, 2*4 元素表示两个至四个元素

  - 可选序列[]:

    - [ message-body ]





# 网络相关工具

- Chrome浏览器Network面板
- Wireshark
- tcpdump
