<div align="center">

<image src="https://github.com/user-attachments/assets/3b85e1ef-35e3-4f95-bf5e-90ca7f8fae13" height="86"/>

# APICORE v2

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Python版本](https://img.shields.io/badge/Python-3.8%2B-brightgreen)
![版本号](https://img.shields.io/badge/Version-2.0.0-blue)

The NEXT-Generation API Configuration & Orchestration Runtime Engine.

**More efficient, all-round capable.**

​​下一代高效、全能的 API 配置与编排运行时规范​格式标准

</div>


> [!WARNING]
>
> 此版本的规范正在研发和测试中，目前暂未投入使用。请转到 [APICORE v1](https://github.com/SRON-org/APICORE/)


## 简介

APICORE 是一个由 SRON 团队 研发的​​统一API配置解决方案​​，通过声明式配置文件实现：

- **🔄 ​广泛兼容性**: APICORE 规范自身具有强大的可扩展性，无论是各种参数或响应格式都可以轻松兼容。
- **⚡ 简明易读性**: APICORE 的标准参数关键词均为日常生活中的通俗用语，简单易懂。
- **📦 ​​描述标准化​**: APICORE 专注于解决多个应用程序之间API配置管理中的碎片化问题，让开发者告别重复对接工作，专注于核心业务逻辑。

## 为什么选择我们的 APICORE

**更灵活、更强大的可扩展性，和标准规范性**

| 特性           | 	APICORE 标准规范                                    | 传统对接方式        | 
| -------------- | --------------------------------------- | ----------------------------------------- |
| **​​开发效率​​**       | **配置文件驱动**          | 手工编写调用代码                  |
| **维护成本​**       | **单点配置全局生效**           | 多处修改难以同步                    |
| **​​错误处理​**       | **统一异常规范**                | 接口差异处理                      |
| **强大生态**       | **基于 JSON ：更方便地拓展生态**                | 需要单独适配每个API的请求    |

### 与 OpenAPI 规范的区别
虽然 APICORE 和 OpenAPI 都致力于解决 API 的描述和使用问题，但两者出发点和核心用途有显著的不同。我们建议你合理地选择 APICORE 与 OpenAPI 有助于使开发更加合理、规范和高效。

1. 适用范围：
OpenAPI 的核心目标是为 RESTful API 提供一个**全面、语言无关**的标准接口描述，而 APICORE 的核心目标是**驱动用户界面** (即 UI) .它通过读取配置文件，将 API 的参数**以用户友好的方式展示在 UI 上**，让最终用户可以动态地编辑参数并发起请求。其的重点在于简化和标准化应用与单个 API 端点的动态交互。

2. 设计思路：
OpenAPI 规范非常详尽和复杂，可以描述整个 API 服务的所有路径 (endpoints)、操作 (GET, POST)、参数、请求体、响应、安全方案 (Authentication)、可重用组件等。而 APICORE 的**结构相对简单，通常一个配置文件只描述一个 API 端点的单次调用**，其包含大量为了优化 UI 展示的字段，如 friendly_name (友好名称)、intro (简介)、icon (图标) 等，而这些并非 OpenAPI 的标准关注点。

3. 响应处理方式：
OpenAPI 侧重于定义不同 HTTP 状态码下完整的响应数据结构 (即 **Schema**) ，APICORE 更侧重于从成功的响应中提取 (extract) 特定数据。其通过 response 对象中的 path 字段，利用**类似 JSONPath 的语法**来精确获取需要展示给用户的数据，例如图片 URL 或特定信息。

4. 特色：
对于需要集成大量第三方、结构各异的简单 API（尤其是那些用于生成内容，如图片、文本的 API）的应用来说，APICORE 提供了一种**标准化的“适配层”**。开发者无需为每个 API 单独编写调用和解析逻辑，只需为它们各创建一个 APICORE 配置文件，应用就可以通过统一的运行时来加载并与之交互，并借助强大的 [**APIKernal**](https://github.com/SRInternet/APIKernal) 项目，仅需几行代码即可实现API从请求到解析值的一步到位。

## 编写

### 手动编写
欢迎访问本仓库 [Wiki](https://github.com/SRON-org/APICORE-2/wiki) 

这里有详细的[编写指南](https://github.com/SRON-org/APICORE-2/wiki/Create-a-New-APICORE-Configuration-File)。通过指南，你可以详细和准确地编写符合 APICORE 规范的API配置

## 生态

开发中……

## 代码补全

开发中……

## 标准和示例

开发中……

## 开放

我们时刻欢迎各位开发者完善和更新协议，欢迎提交 Pull Request 来改进 APICORE ！

## 协议

[MIT](./LICENSE)
