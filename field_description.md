# 字段说明文档 Field Description

本文档详细说明 `terminology.csv` 主术语表中各字段的含义、取值规范和填写要求。

---

## 字段总览

| 字段名 | 类型 | 是否必填 | 说明 |
|---|---|---|---|
| `id` | 字符串 | 是 | 术语唯一编号 |
| `domain` | 枚举值 | 是 | 所属技术领域 |
| `en_term` | 字符串 | 是 | 英文原词 |
| `zh_preferred` | 字符串 | 是 | 首选中文译名 |
| `zh_acceptable` | 字符串 | 否 | 可接受次选译名 |
| `zh_forbidden` | 字符串 | 否 | 禁用译名及原因（逗号分隔） |
| `definition_zh` | 字符串 | 是 | 中文技术定义 |
| `applicable_context` | 字符串 | 是 | 适用工况/场景描述 |
| `risk_notes` | 字符串 | 是 | 误用风险提示 |
| `source` | 字符串 | 是 | 术语来源文献缩写 |

---

## 字段详细说明

### `id` — 术语编号

格式：`领域前缀-三位数字`，例如 `A-001`、`S-012`、`T-005`。

领域前缀对应：
- `A` → aerodynamics（空气动力学）
- `S` → suspension_chassis（悬挂与底盘）
- `P` → powertrain_ers（动力总成与ERS）
- `T` → tyres_thermal（轮胎与热管理）
- `O` → strategy_operations（策略与运营）

---

### `domain` — 技术领域

取值限于以下五个枚举值（小写，下划线连接）：

| 取值 | 对应领域 |
|---|---|
| `aerodynamics` | 空气动力学 |
| `suspension_chassis` | 悬挂与底盘结构 |
| `powertrain_ers` | 动力总成与能量回收系统 |
| `tyres_thermal` | 轮胎与热管理 |
| `strategy_operations` | 赛事策略与操作 |

---

### `en_term` — 英文原词

填写最简洁的英文术语形式，括注缩写时格式为：`full term (ABBREVIATION)`，例如：`Energy Recovery System (ERS)`。

---

### `zh_preferred` — 首选中文译名

填写在本术语库中统一使用的中文标准译名，即"同物同名"原则下的唯一推荐表达。  
首选译名应符合以下标准：
1. 符合目标读者（工程技术读者）的阅读习惯
2. 与FIA官方中文文件保持一致（如有）
3. 在围场和技术媒体中已具有一定通用度

---

### `zh_acceptable` — 可接受次选译名

在特定上下文（如历史文献引用、口语场合）中可接受使用的非首选译名。  
若无次选，留空。

---

### `zh_forbidden` — 禁用译名

会导致技术误解的错误译名，格式为：`禁用词（原因说明）`。  
例如：`轴心冷却（暗示冷却器集中在轴心点，与中轴线布局含义不符）`

---

### `definition_zh` — 中文技术定义

对该术语的精确中文技术定义，应包含：
- 该术语指代的具体对象或现象
- 其在F1工程系统中的作用或位置
- 与相关概念的关键区分

定义应控制在100字以内，以简洁准确为原则。

---

### `applicable_context` — 适用工况/场景

描述该术语在何种工程或策略情境下使用，帮助译者判断选词是否合适。  
例如：`适用于底板气动效率讨论、地面效应规则下的赛车开发报道`

---

### `risk_notes` — 误用风险提示

指出使用该术语时最常见的翻译或理解错误，以及如何避免。  
格式建议：`不应与X混用，因为...` 或 `与Y的区别是...`

---

### `source` — 来源文献缩写

| 缩写 | 完整来源 |
|---|---|
| `RE2017` | Racecar Engineering, September 2017 |
| `RE2024` | Racecar Engineering, February 2024 |
| `FIA2024` | FIA Formula One Technical Regulations 2024 |
| `RCVD` | Milliken & Milliken, Race Car Vehicle Dynamics (1995) |
| `PADDOCK` | 围场口语记录（作者一手记录，匿名处理） |
