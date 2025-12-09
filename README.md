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

APICORE 是一个由 SRON 团队 研发的​，**面向 UI 的、轻量级 API 交互**描述规范。

遵循 **"Optional Complexity"（可选复杂性）** 的设计理念，开发者只需编写一个简单的 `.api.json` 文件，即可描述从简单的 HTTP 请求到包含鉴权、重试机制、参数动态引用、错误分支处理**的复杂 API 交互逻辑。

## 核心特性

- **🎨 UI 优先的元数据系统**：通过 `friendly_name`, `placeholder`, `tooltip`, `text_secret` 等字段，直接指导前端渲染出对人类友好的交互表单。
- **✨ 参数类型丰富**：参数 (`parameters`) 配置字段支持整数 (`integer`)、浮点数 (`number`)、列表 (`list`)、选择项 (`enum`) 等多种参数类型，前端交互更加直观、便捷。
- **🧠 智能状态处理**：利用 `handlers` 字段构建状态机，针对 401 (鉴权失败)、429 (限流)、200 (成功) 定义不同的行为分支，支持自动重试 (`retry`)、错误提取 (`extract`) 和 友好提示 (`message`) 等丰富操作。
- **🔗 动态变量注入**：支持在 URL、Header 和 Body 中使用 `{{parameters.api_key}}` 语法引用用户输入。无论是 Bearer Token 还是自定义签名头，都能灵活配置。
- **⚙️ 全局行为控制**：通过 `configs` 模块统一管理超时策略、默认请求头和速率限制，将业务逻辑与底层网络配置解耦。

## 为什么选择我们的 APICORE v2

**更灵活、更强大的可扩展性，和标准规范性**

| 特性维度 | 🚀 APICORE v2 | 📦 其他格式/协议 | 📜 OpenAPI (Swagger) |
| :--- | :--- | :--- | :--- |
| **核心定位** | **UI 驱动 & 交互引擎** | 特定业务数据的打包格式 | 后端接口定义 & 文档标准 |
| **上手难度** | **极低** (单文件，结构扁平) | **一般**  | **极高** (结构极其复杂，嵌套深) |
| **交互逻辑** | **内置状态机** (支持重试、分支处理) | **较弱 (一般的数据映射等)** | 无 (仅描述静态结构) |
| **UI 表现力** | **丰富** (支持图标、占位符、掩码) | **一般 (仅基础标签)** | 差 (仅 Description，生成的 UI 冰冷) |
| **分发方式** | **拖拽即用** (.json 单文件) | **单文件或集合打包** | 需代码生成或专门的阅读器 |
| **适用场景** | **API 商店、工具箱、低代码平台** | 特定的垂直领域 App | 企业级开发、前后端联调 |
| **灵活性** | **高** (变量动态注入 Header/Body) | 低 (通常写死鉴权方式) | 中 (需配合 Codegen 使用) |

## 编写

### 手动编写
欢迎访问本仓库 [Wiki](https://github.com/SRON-org/APICORE-2/wiki) 

这里有详细的[编写指南](https://github.com/SRON-org/APICORE-2/wiki/Create-a-New-APICORE-Configuration-File)。通过指南，你可以详细和准确地编写符合 APICORE 规范的API配置

## 应用场景

[**壁纸生成器 NEXT**](https://github.com/SRInternet-Studio/Wallpaper-generator/)：下一代个性化聚合图片生成平台

[**小树壁纸Next**](https://github.com/shu-shu-1/Little-Tree-Wallpaper-Next-Flet)：一款多功能桌面壁纸应用程序

以及更多与API请求相关的应用程序，均与 APICORE v2 规范极其搭配哦

## 代码补全

开发中……

## 标准和示例

开发中……

## 开放

我们时刻欢迎各位开发者完善和更新协议，欢迎提交 Pull Request 来改进 APICORE ！

## 协议

[MIT](./LICENSE)
