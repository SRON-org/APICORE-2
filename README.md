<div align="center">

<img width="86" height="86" alt="APICORE娘-圆角图标" src="https://github.com/user-attachments/assets/17814599-a2af-4605-8a18-be7d1fef2c8d" />

# APICORE v2.1

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Python版本](https://img.shields.io/badge/Python-3.8%2B-brightgreen)
![版本号](https://img.shields.io/badge/Version-2.1.0-lightblue)

The NEXT-Generation API Configuration & Orchestration Runtime Engine.

**More efficient, all-round capable.**

​一个专为人类与 API 在 UI 界面上交互而诞生的 API 配置与编排运行时规范​格式标准

</div>


> [!NOTE]
>
> 此版本的规范正在公测阶段。若要寻找已经投入使用的版本，请转到 [APICORE v1](https://github.com/SRON-org/APICORE/)


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

## 生态和应用场景

[**APICORE_Python**](https://github.com/SRON-org/APICORE_Python/tree/main)：在 Python 上提供对使用 APICORE **v2.1, v2.0** 甚至是 **v1.0** 规范的文件的进行解析

[**壁纸生成器 NEXT**](https://github.com/SRInternet-Studio/Wallpaper-generator/)：下一代个性化聚合图片生成平台

[**小树壁纸Next**](https://github.com/shu-shu-1/Little-Tree-Wallpaper-Next-Flet)：一款多功能桌面壁纸应用程序

以及更多与API请求相关的应用程序，均与 APICORE v2 规范极其搭配哦

## 代码补全

通过引入 [Schema 文件（已兼容 v2.1）](https://raw.githubusercontent.com/SRON-org/APICORE-2/refs/heads/main/APICORE.v2.Schema.json)，编辑器将会为你开启自动补全、实时纠错等功能，极大地提升你编写配置文件的体验。

### 临时配置

#### JSON 格式
1. 若要本地开发，先将 [APICORE.v2.Schema.json](https://github.com/SRON-org/APICORE-2/blob/main/APICORE.v2.Schema.json) 保存到你的 `.api.json` 配置文件根目录中
2. 在你的配置文件头部添加 `$schema` 字段，指向该文件的本地路径或远程路径

#### YAML 格式

1. 先将 [APICORE.v2.Schema.json](https://github.com/SRON-org/APICORE-2/blob/main/APICORE.v2.Schema.json) 保存到你的 `.api.yaml` 配置文件根目录中
2. 在你的配置文件头部添加 `# yaml-language-server: $schema=./APICORE.v2.Schema.json`

#### 本地开发示例
```json
{
  "$schema": "./APICORE.v2.Schema.json",
}
```

#### 远程开发示例
```json
{
  "$schema": "https://raw.githubusercontent.com/SRON-org/APICORE-2/refs/heads/main/APICORE.v2.Schema.json",
}
```
### 全局配置

#### VS Code 配置方法
1. 在或创建 .vscode/settings.json 文件
2. 添加以下配置：
```json
{
  "json.schemas": [
    {
      "fileMatch": ["*.api.json"],
      "url": "https://raw.githubusercontent.com/SRON-org/APICORE-2/refs/heads/main/APICORE.v2.Schema.json"
    }
  ],
  "yaml.schemas": {
    "https://raw.githubusercontent.com/SRON-org/APICORE-2/refs/heads/main/APICORE.v2.Schema.json": "*.api.yaml"
  }
}
```

### JetBrains IDE 配置方法
1. 打开 Preferences > Languages & Frameworks > Schemas and DTDs > JSON Schema Mappings
2. 添加新映射：
- Schema file or URL: https://raw.githubusercontent.com/SRON-org/APICORE-2/refs/heads/main/APICORE.v2.Schema.json
- File path pattern: *.api.json
- Schema version: Draft 7

## 标准和示例

编码: UTF-8

参考：[完整示例](https://github.com/SRON-org/APICORE-2/wiki/Create-a-New-APICORE-Configuration-File#7-%E5%AE%8C%E6%95%B4%E7%A4%BA%E4%BE%8B)

## 开放

我们时刻欢迎各位开发者完善和更新协议，欢迎提交 Pull Request 来改进 APICORE ！

## 协议

[MIT](./LICENSE)
