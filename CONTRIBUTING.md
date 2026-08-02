# APICORE 规范贡献指南

> **版本**: v2.1
> 
> **最后更新**: 2026-08-02
> 
> **适用范围**: 希望参与 APICORE 协议规范演进的贡献者

---

## 目录

1. [概述与价值观](#1-概述与价值观)
2. [修改规范的流程 (RFC)](#2-修改规范的流程-rfc)
3. [版本号变更规则 (SemVer)](#3-版本号变更规则-semver)
4. [Schema 校验测试](#4-schema-校验测试)
5. [提交规范 (Commit Message)](#5-提交规范-commit-message)
6. [行为准则](#6-行为准则)

---

## 1. 概述与价值观

APICORE 是一个开放的中立协议，旨在通过声明式配置文件描述 API 交互逻辑。我们欢迎所有形式的贡献——无论是修正拼写错误、提出新字段、还是质疑现有设计。

### 核心设计原则

在提出任何修改建议前，请确保你的提案符合以下原则：

1. **可选复杂性 (Optional Complexity)**：简单的事应该简单，复杂的事应该可能。新字段不应增加基础用例的负担。
2. **向下兼容优先**：任何修改不应破坏现有 `.api.json` 配置文件的解析。
3. **实现无关**：规范描述的是"是什么"，而非"怎么实现"。不应在规范中规定特定编程语言或框架的行为。
4. **安全第一**：新功能必须通过威胁模型审查，参见 [SECURITY.md](./SECURITY.md)。

---

## 2. 修改规范的流程 (RFC)

APICORE 采用 **RFC (Request for Comments)** 流程来管理所有规范变更。无论是新增字段、调整语义还是废弃旧特性，都必须经过以下步骤：

### 2.1 流程概览

```
提出问题 (Issue)
    │
    ▼
社区讨论 (≥ 7 天)
    │
    ▼
核心维护者评审
    │
    ▼
起草 RFC 提案 (Pull Request)
    │
    ▼
最终表决 (≥ 2 名维护者同意)
    │
    ▼
合并 → 更新规范文档 + Schema + Changelog
```

### 2.2 第一步：提出问题 (Issue)

在提交任何 PR 之前，请先在 [GitHub Issues](https://github.com/SRON-org/APICORE-2/issues) 中创建一个 Issue，描述你的想法。

**Issue 标题格式**：
```
[RFC] 简短描述你的提案
```

**Issue 正文必须包含**：

```markdown
### 动机 (Motivation)
描述当前规范中存在的痛点或缺失，以及为什么需要修改。

### 提案概述 (Proposal)
用一两段话描述你建议的变更。

### 向后兼容性 (Backward Compatibility)
明确说明此变更是否破坏现有配置文件的解析。

### 示例 (Examples)
提供修改前后的配置示例对比。

### 替代方案 (Alternatives)
描述你考虑过但未采纳的其他方案，以及未被采纳的原因。
```

### 2.3 第二步：社区讨论

- Issue 发布后，社区成员和核心维护者将进行公开讨论
- 讨论周期**不少于 7 天**，以确保不同时区的贡献者都能参与
- 核心维护者可能在讨论中提出修改建议或要求补充细节
- 如果讨论中产生重大分歧，维护者可能发起一次**非正式投票**（👍 / 👎 reactions）以判断社区共识

### 2.4 第三步：起草 RFC 提案 (Pull Request)

当社区讨论趋于共识后，你可以提交一个 Pull Request 来正式推进提案。

**PR 必须包含以下文件变更**：

| 文件 | 内容 |
|------|------|
| `Create-a-New-APICORE-Configuration-File.md` | 更新规范文档，在对应章节添加/修改字段说明 |
| `APICORE.v2.Schema.json` | 更新 JSON Schema 定义，包含新增字段的约束 |
| 新增/更新示例配置文件 | 在规范文档中添加展示新特性的示例 |
| `CHANGELOG.md`（如有） | 在更新日志中记录本次变更 |

**PR 标题格式**：
```
[RFC] 实现 #Issue编号 - 提案标题
```

### 2.5 第四步：最终表决

- PR 必须获得**至少 2 名核心维护者**的 Approve 方可合并
- 如果 PR 涉及破坏性变更（Breaking Change），需要**至少 3 名核心维护者**同意
- 维护者有权对 PR 提出修改要求（Request Changes），贡献者应在合理时间内响应
- 如果 PR 在 30 天内无活动，维护者可能关闭该 PR（可重新打开）

### 2.6 快速通道（Fast Track）

以下类型的变更可跳过 Issue 讨论阶段，直接提交 PR：

- 修正文档中的拼写错误、格式错误、死链
- 在不改变语义的前提下优化措辞
- 更新示例代码以反映已有规范的正确用法

> 快速通道 PR 仍需至少 1 名维护者 Approve 方可合并。

---

## 3. 版本号变更规则 (SemVer)

APICORE 协议严格遵循 **语义化版本 (Semantic Versioning)** 规范。`APICORE_version` 字段使用 `MAJOR.MINOR` 格式（如 `2.1`）。

### 3.1 版本号递增规则

| 变更类型 | 版本号 | 示例 | 说明 |
|---------|--------|------|------|
| **新增可选字段** | `MINOR` +1 | `2.1` → `2.2` | 新增不影响旧配置解析的字段、属性或枚举值 |
| **新增可选配置项** | `MINOR` +1 | `2.1` → `2.2` | 如 `configs` 下新增一个可选子对象 |
| **扩展字段类型** | `MINOR` +1 | `2.1` → `2.2` | 如 `friendly_name` 从仅支持 `string` 扩展到支持 `string | object`（i18n） |
| **废弃 (Deprecate) 字段** | `MINOR` +1 | `2.1` → `2.2` | 标记字段为 `DEPRECATED`，但仍可解析 |
| **放宽约束** | `MINOR` +1 | `2.1` → `2.2` | 如将 `required` 改为可选 |
| **移除已废弃字段** | `MAJOR` +1 | `2.x` → `3.0` | 彻底删除已标记 `DEPRECATED` 的字段 |
| **收紧约束** | `MAJOR` +1 | `2.x` → `3.0` | 如将可选字段改为必填 |
| **修改字段语义** | `MAJOR` +1 | `2.x` → `3.0` | 改变已有字段的含义或行为 |
| **删除字段** | `MAJOR` +1 | `2.x` → `3.0` | 直接删除未经过废弃期的字段 |

### 3.2 废弃 (Deprecation) 策略

当一个字段被标记为废弃时：

1. **规范文档**：在该字段的说明中标注 `**DEPRECATED**`，并指出替代方案
2. **JSON Schema**：在字段的 `description` 中注明 `DEPRECATED`，但保留其定义
3. **解析器**：接受该字段但不依赖它，同时输出 `warning` 级别的提示
4. **废弃期**：一个字段从标记 `DEPRECATED` 到正式移除，必须经过至少一个 `MAJOR` 版本的过渡期

示例——`friendly_value` 在 v2.1 被标记为废弃，将在 v3.0 中移除：
```
v2.0: friendly_value 为 enum 类型必填字段
v2.1: friendly_value 标记为 DEPRECATED，推荐使用 options + friendly_options
v3.0: friendly_value 正式移除
```

### 3.3 配置文件自身版本 (`version`)

配置文件根节点中的 `version` 字段（如 `"version": "1.2.0"`）遵循标准的三段式 SemVer（`MAJOR.MINOR.PATCH`），由配置文件作者自行管理，与协议版本 `APICORE_version` 独立。

---

## 4. Schema 校验测试

所有对 `APICORE.v2.Schema.json` 的修改，必须在提交 PR 前通过以下校验流程。

### 4.1 校验要求

| 测试项 | 要求 | 工具 |
|--------|------|------|
| **Schema 自身合法性** | Schema 文件必须是合法的 JSON Schema Draft 2020-12 | `ajv`, `check-jsonschema` |
| **正向测试** | 至少 3 个合法的示例配置文件能通过 Schema 校验 | `ajv validate -s schema.json -d example.json` |
| **负向测试** | 至少 2 个故意写错的配置文件被 Schema 正确拒绝 | 同上，预期返回 validation error |
| **Python 校验脚本** | 通过规范文档中提供的 `validate_apicore_v2_1()` 脚本校验 | 见规范文档中的验证工具 |

### 4.2 运行本地校验

```bash
# 安装依赖
npm install -g ajv-cli
# 或
pip install check-jsonschema

# 校验 Schema 自身合法性
ajv compile -s APICORE.v2.Schema.json

# 正向测试：合法的示例配置应该通过
ajv validate -s APICORE.v2.Schema.json -d examples/valid_example_1.api.json
ajv validate -s APICORE.v2.Schema.json -d examples/valid_example_2.api.json
ajv validate -s APICORE.v2.Schema.json -d examples/valid_example_3.api.json

# 负向测试：非法的配置文件应该被拒绝
ajv validate -s APICORE.v2.Schema.json -d examples/invalid_example_1.api.json  # 预期报错
ajv validate -s APICORE.v2.Schema.json -d examples/invalid_example_2.api.json  # 预期报错

# Python 校验脚本
python validate_v2_1.py examples/valid_example_1.api.json
```

### 4.3 示例测试文件结构

```
APICORE-2/
├── APICORE.v2.Schema.json
├── examples/
│   ├── valid/
│   │   ├── minimal.api.json          # 最小合法配置
│   │   ├── full_featured.api.json    # 全特性配置
│   │   └── i18n_example.api.json     # 国际化示例
│   └── invalid/
│       ├── missing_required.api.json # 缺少必填字段
│       ├── bad_version.api.json      # 版本号非法
│       └── bad_action.api.json       # action 类型非法
└── tests/
    └── validate_schema.py
```

### 4.4 CI 自动化

建议在仓库的 CI 流程（GitHub Actions）中加入以下步骤：

```yaml
# .github/workflows/schema-check.yml
name: Schema Validation

on:
  pull_request:
    paths:
      - 'APICORE.v2.Schema.json'
      - 'examples/**'

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Validate JSON Schema
        uses: cardinalby/schema-validator-action@v3
        with:
          schema: APICORE.v2.Schema.json
      - name: Positive Tests
        run: |
          for f in examples/valid/*.api.json; do
            npx ajv validate -s APICORE.v2.Schema.json -d "$f" || exit 1
          done
      - name: Negative Tests
        run: |
          for f in examples/invalid/*.api.json; do
            npx ajv validate -s APICORE.v2.Schema.json -d "$f" && exit 1 || true
          done
```

---

## 5. 提交规范 (Commit Message)

APICORE 仓库使用 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

```
<type>(<scope>): <简短描述>

<详细描述（可选）>

<关联 Issue（可选）>
```

### 常用 Type

| Type | 用途 |
|------|------|
| `feat` | 新增规范字段或特性 |
| `fix` | 修正规范文档中的错误 |
| `docs` | 仅文档修改（不涉及规范变更） |
| `deprecate` | 标记字段为废弃 |
| `remove` | 移除已废弃字段（MAJOR 版本） |
| `schema` | JSON Schema 文件修改 |
| `test` | 新增或修改测试用例 |
| `chore` | 构建、CI 等杂项变更 |

### 示例

```
feat(parameter): 新增 show_if 条件联动字段

为 parameters 增加 show_if 配置项，支持基于其他参数值的 UI 显隐控制。
支持 equals 和 in 两种条件判断。

Closes #42
```

```
deprecate(parameter): 标记 friendly_value 为废弃

推荐使用 options + friendly_options 替代 friendly_value。
该字段将在 v3.0 中正式移除。

Closes #58
```

---

## 6. 行为准则

APICORE 项目遵循 [Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) 行为准则。

### 核心准则

- **尊重**：对不同观点和经验的贡献者保持尊重
- **建设性**：批评应针对提案本身，而非提案者个人
- **协作**：我们的目标是共同改进协议，而非赢得争论
- **耐心**：不是所有人都在同一时区或有相同的可用时间

### 违反行为准则的后果

维护者有权对违反行为准则的参与者采取以下措施：
1. 口头警告
2. 临时禁言
3. 永久封禁

---

> **感谢你为 APICORE 协议做出的贡献！每一份 Issue、每一个 PR、每一次讨论都在推动这个协议变得更好。**
