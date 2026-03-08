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
---

## 术语预览 Terminology Preview

以下为各领域代表性术语样例。完整284条词条见 [`data/terminology.csv`](./data/terminology.csv)。

### 🌬️ 空气动力学 Aerodynamics

| 英文原词 | 首选译名 | 禁用译名 | 简要定义 |
|---|---|---|---|
| ground effect | 地面效应 | 地面摩擦效应 | 利用赛车底部与赛道之间气流加速产生低压区，从而生成下压力的气动现象 |
| downforce | 下压力 | 下压 | 气流在赛车各气动面产生的垂直向下气动力，是弯道速度的核心参数 |
| centreline cooling | 中轴线冷却 | 中央冷却/轴心冷却 | 将主要冷却器集中布置于车辆纵向中轴附近，释放侧箱气动通道的冷却方案 |
| porpoising | 海豚跳 | 底板振荡/颠簸 | 地面效应规则下赛车底板气流周期性分离引起的车身高频垂向振荡 |
| desensitised aerodynamics | 气动去敏化 | 稳定气动设计 | 使气动性能对车身姿态变化不敏感、在更宽工况范围内保持稳定输出的开发策略 |
| rake | 倾角/车身纵倾 | 俯仰角 | 赛车前低后高（或相反）的纵向倾斜姿态，通过前后离地间隙差实现 |

### 🔧 悬挂与底盘 Suspension & Chassis

| 英文原词 | 首选译名 | 禁用译名 | 简要定义 |
|---|---|---|---|
| compliance | 顺应性 | 柔性变形/松动 | 悬挂连接件在载荷下允许的微小弹性变形特性，适当顺应性可提高操控一致性 |
| anti-dive | 抗俯冲 | 防前倾 | 通过悬挂几何使制动时产生对抗前俯力矩，维持车身平台稳定性 |
| anti-squat | 抗蹲尾 | 防后沉 | 通过悬挂几何使加速时产生对抗后蹲力矩，减少加速姿态变化 |
| pushrod | 推杆 | 前推连杆 | 连接悬挂下部与弹簧/减震器总成的传力杆件，车轮向上时受压 |
| pullrod | 拉杆 | 后拉连杆 | 连接悬挂上部与弹簧/减震器总成的传力杆件，车轮向上时受拉，有助于降低重心 |
| torsional stiffness | 扭转刚度 | 抗扭刚性 | 结构抵抗扭转变形的能力（Nm/deg），直接影响悬挂几何有效性 |

### ⚡ 动力总成与ERS Powertrain & ERS

| 英文原词 | 首选译名 | 禁用译名 | 简要定义 |
|---|---|---|---|
| power unit (PU) | 动力单元 | 发动机 | 包含ICE、涡轮增压器、MGU-K/H及储能单元的F1混合动力系统整体 |
| ERS deployment | ERS能量部署 | 能量释放 | 在特定赛道区段将电池电能通过MGU-K释放提供额外动力的策略操作 |
| MGU-K | MGU-K（动能电机发电单元） | K电机 | 连接传动系统、制动时回收动能、加速时释放电能的电机单元，最大120kW |
| cost cap | 成本帽 | 预算上限 | FIA自2021年引入的年度运营支出上限，限制气动开发配额及零件迭代频次 |
| charge air cooler | 增压空气中冷器 | 中冷器 | 对涡轮增压后高温进气进行冷却的热交换器，提升充气效率 |

### 🏎️ 轮胎与热管理 Tyres & Thermal Management

| 英文原词 | 首选译名 | 禁用译名 | 简要定义 |
|---|---|---|---|
| thermal degradation | 热衰退 | 热衰减/热磨损 | 轮胎橡胶高温下抓地力下降的现象，**降温后可部分恢复**（区别于不可逆磨损） |
| tyre window | 轮胎工作窗口 | 最佳温度区间 | 轮胎配合物能正常提供最大抓地力的工作温度范围，是策略决策的核心边界 |
| graining | 起粒 | 搓皮/橡胶剥落 | 轮胎表面橡胶在滑动中形成小颗粒翻滚的磨损形式，通常因胎温不足引起 |
| contact patch | 接触印痕 | 接触面积 | 轮胎与赛道实际接触的橡胶区域，影响最大摩擦力和侧向抓地力上限 |
| blistering | 起泡 | 鼓泡 | 轮胎严重过热时内部气泡破裂形成表面鼓泡，通常须立即进站更换 |

### 📊 策略与运营 Strategy & Operations

| 英文原词 | 首选译名 | 禁用译名 | 简要定义 |
|---|---|---|---|
| undercut | 内停策略 | 提前进站 | 早于对手进站换新胎，利用新胎圈速优势在出站口完成超越的比赛策略 |
| overcut | 外停策略 | 延迟进站 | 晚于对手进站、利用持续积累时间差完成超越的比赛策略 |
| free stop | 免费进站 | 无代价进站 | 安全车/VSC期间进站，因全场降速使进站时间损失大幅降低的策略机会 |
| platform control | 平台控制 | 车身姿态控制 | 精确控制赛车车身姿态（离地间隙、俯仰、横滚）稳定性，使气动系统持续高效工作 |
| tyre management | 轮胎管理 | 轮胎保护 | 通过驾驶风格调整和策略规划延长轮胎寿命并保持工作窗口的综合技术工作 |

> 💡 **使用提示**：`zh_forbidden` 列标注了会导致技术误解的错误译名，翻译时应严格避免。每条术语的完整定义、适用工况及误用风险详见CSV文件。
