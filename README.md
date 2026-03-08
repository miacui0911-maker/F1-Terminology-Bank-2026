# F1 Chinese-English Terminology Database
# F1 赛车工程汉英双语术语库

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Terms](https://img.shields.io/badge/Terms-280%2B-blue)](./data/terminology.csv)
[![Language](https://img.shields.io/badge/Language-EN%20%7C%20ZH-orange)](./data/)

> 本项目为开源 F1 赛车工程领域汉英双语术语库，源自华东理工大学翻译专业硕士学位论文实践项目：《F1 高技术文本英译汉本地化实践报告——以〈Racecar Engineering〉三篇文章为例》。  
> 维护者：崔紫云（Mia Cui）| 华东理工大学外国语学院 MTI 2024 级

---

## 项目背景 Project Background

Formula 1 赛车工程文本（如 *Racecar Engineering* 杂志）是技术密度极高的专业媒体语料，涉及空气动力学、悬挂动力学、混合动力系统、轮胎热管理等多个工程子领域。由于国内尚无系统性的 F1 工程领域汉英术语对照资源，该类文本的翻译长期存在"术语漂移"（同一概念多种译名并存）和"概念错位"（字面对译导致技术含义失真）等问题。

本项目旨在通过系统化的术语收集、多源校订与开源共享，为 F1 赛车工程文本的中文本地化提供可靠的术语参考基准。

---

## 数据来源 Data Sources

术语条目来源于以下多类资料的交叉校订：

| 来源类型 | 具体来源 |
|---|---|
| 专业期刊 | *Racecar Engineering*（2017、2024 年期） |
| 官方法规 | FIA Formula One Technical Regulations 2024 |
| 工程参考书 | Milliken & Milliken, *Race Car Vehicle Dynamics* (SAE, 1995) |
| 围场口语记录 | 作者参加上海、新加坡、阿布扎比等大奖赛围场访谈记录 |
| 工程师表述 | VCARB 车队技术人员一线口头表达（匿名处理） |

---

## 文件结构 Repository Structure

```
F1-Chinese-English-Terminology-Database/
├── README.md                        # 本文件
├── data/
│   ├── terminology.csv              # 主术语表（CSV，UTF-8）
│   └── terminology_by_domain/
│       ├── aerodynamics.csv         # 空气动力学子库
│       ├── suspension_chassis.csv   # 悬挂与底盘子库
│       ├── powertrain_ers.csv       # 动力总成与ERS子库
│       ├── tyres_thermal.csv        # 轮胎与热管理子库
│       └── strategy_operations.csv  # 策略与运营子库
├── docs/
│   ├── field_description.md         # 字段说明文档
│   ├── contribution_guide.md        # 贡献指南
│   └── usage_examples.md            # 使用示例
└── LICENSE
```

---

## 字段说明 Field Description

主术语表 `terminology.csv` 包含以下字段：

| 字段名 | 说明 |
|---|---|
| `id` | 术语编号（如 A-001） |
| `domain` | 所属领域（aerodynamics / suspension / powertrain / tyres / strategy） |
| `en_term` | 英文原词 |
| `zh_preferred` | 首选中文译名 |
| `zh_acceptable` | 可接受次选译名（可为空） |
| `zh_forbidden` | 禁用译名及原因 |
| `definition_zh` | 中文技术定义 |
| `applicable_context` | 适用工况/场景 |
| `risk_notes` | 误用风险提示 |
| `source` | 术语来源文献缩写 |

---

## 快速使用 Quick Start

```python
import pandas as pd

df = pd.read_csv('data/terminology.csv', encoding='utf-8')

# 查找某个英文术语
result = df[df['en_term'] == 'thermal degradation']
print(result[['en_term', 'zh_preferred', 'definition_zh']].to_string())

# 按领域筛选
aero_terms = df[df['domain'] == 'aerodynamics']
print(f"空气动力学领域术语共 {len(aero_terms)} 条")
```

---

## 术语统计 Statistics

| 领域 | 术语数量 |
|---|---|
| 空气动力学（Aerodynamics） | 68 |
| 悬挂与底盘（Suspension & Chassis） | 72 |
| 动力总成与ERS（Powertrain & ERS） | 54 |
| 轮胎与热管理（Tyres & Thermal Management） | 49 |
| 策略与运营（Strategy & Operations） | 41 |
| **合计** | **284** |

---

## 引用 Citation

如在学术论文或项目中使用本术语库，请按以下格式引用：

```
崔紫云. F1 赛车工程汉英双语术语库 [DB/OL]. GitHub, 2025.
https://github.com/miacui0911-maker/F1-Chinese-English-Terminology-Database
```

---

## 贡献 Contributing

欢迎具有 F1 工程背景或赛车技术翻译经验的贡献者参与完善本术语库。详见 [贡献指南](./docs/contribution_guide.md)。

主要贡献方式：
- 提交 Issue 指出术语错误或缺漏
- 通过 Pull Request 新增或修订条目
- 提供围场/工程师一线表达的口语记录

---

## 许可证 License

本项目采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 许可证。使用时请注明来源。

---

## 免责声明 Disclaimer

本术语库为学术研究目的建设，具体声明如下：

1. **内容来源**：本库术语定义综合参考了《Racecar Engineering》杂志、FIA官方技术法规及公开工程文献，所有引用内容版权归原作者所有。本库仅提供术语的中文译名、定义摘要及使用建议，不涉及原文章的大段复制或完整转载。

2. **学术性质**：本项目为华东理工大学翻译专业硕士学位论文的配套实践成果，不具有商业目的，不构成任何商业建议或技术咨询服务。

3. **准确性说明**：F1工程技术领域术语随规则迭代和业界用法持续演变，本库条目反映截至2025年的参考资料状态。维护者不对因使用本库译名而产生的翻译错误或技术误解承担法律责任，建议在正式出版或工程应用场景中另行核实。

4. **商标说明**：Formula 1、F1、FIA等名称及相关标志均为其各自权利人的注册商标，本项目与Formula One Group、FIA或任何F1车队不存在任何官方关联。

5. **许可证范围**：本库数据内容（CSV文件及说明文档）采用CC BY 4.0许可证。引用或二次开发时须注明来源，不得暗示原作者为衍生作品背书。

> This database is built for academic purposes as part of an MTI thesis project. It does not reproduce copyrighted article content and has no affiliation with Formula One Group, FIA, or any F1 team. All trademarks belong to their respective owners.
