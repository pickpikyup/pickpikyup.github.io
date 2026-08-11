---
layout: post
title: "美国制裁等级体系全景拆解：从全面禁运到产品管控"
subtitle: "基于 BIS Federal Register、EAR Part 744/746、OFAC 法规原文"
date: 2026-08-11
author: "X师傅"
header-img: "img/post-bg-sanctions.jpg"
catalog: true
tags:
  - 制裁
  - 出口管制
  - EAR
  - OFAC
  - 半导体
---

## 一、双体系：BIS 和 OFAC 的管辖边界

美国制裁涉及两套独立但有交叉的法律框架：

| 机构 | 所属部门 | 核心工具 | 法律依据 | 核心效果 |
|------|----------|----------|----------|----------|
| **BIS** | 商务部 | Entity List | 15 CFR Part 744, Supp. No. 4 | 出口管制 — 不卖东西给你 |
| **OFAC** | 财政部 | SDN List | 31 CFR Chapter V | 资产冻结 + 交易禁止 — 不让你用美元 |

BIS 管货，OFAC 管钱。

引用原文定义：

> "The Entity List identifies entities for which there is reasonable cause to believe, based on specific and articulable facts, that the entities have been involved, are involved, or pose a significant risk of being or becoming involved in activities contrary to the national security or foreign policy interests of the United States, pursuant to §744.11(b)."

— *Federal Register, Expansion of End-User Controls, Sep 30, 2025*

一句话翻译：只要 BIS 有"合理理由"认为你可能危害美国国家安全，就能把你拉进黑名单。

---

## 二、制裁全景：T0 到 T8

严格度从高到低排列：

```
T0  全面禁运 (OFAC Comprehensive Sanctions)      — 国家级封锁
T1  SDN 封锁 (OFAC SDN + BIS §744.8)              — 个人/实体级封锁
T2  华为级 — Entity List + FN1 FDP + Presumption of Denial  — 最高单实体级别
T3  SMIC级 — Entity List + FN5 FDP + 先进制程推定拒绝
T4  标准 Entity List — Presumption of Denial      — 推定拒绝
T5  Entity List — Case-by-Case Review              — 逐案审查
T6  Military End-User (MEU) List                   — 特定物项管控
T7  Unverified List (UVL)                          — 待核查
T8  产品/目的地管控 — Advanced Computing & SME Controls
```

---

## 三、逐级拆解

### T0: 全面禁运 — OFAC Comprehensive Embargo

**法律依据**：IEEPA + 各类 Executive Orders + 31 CFR Part 500 系列

**制裁行动**：几乎禁止一切涉及该国的贸易、金融交易、资产转移。美国人/美国境内完全不得参与。

**许可审查**：基本不存在，推定拒绝全部交易。

**被制裁对象**：

| 国家/地区 | OFAC 法规 |
|-----------|-----------|
| 伊朗 (Iran) | 31 CFR Part 560 |
| 朝鲜 (North Korea) | 31 CFR Part 510 |
| 叙利亚 (Syria) | 31 CFR Part 542 |
| 古巴 (Cuba) | 31 CFR Part 515 |
| 克里米亚 / 顿涅茨克 / 卢甘斯克 | 31 CFR Part 589 |

**影响**：完全隔绝。没有任何合法渠道获得美国技术、资金、市场。经济基础被直接摧毁。

---

### T1: SDN 封锁制裁 — OFAC Specially Designated Nationals

**法律依据**：31 CFR Chapter V

**制裁行动**：

1. 所有在美资产或被美国人控制的资产**立即冻结**（blocked）
2. 美国人**禁止**与 SDN 进行任何交易
3. **50% 规则**：SDN 持股 ≥50% 的子公司自动被视为 SDN（31 CFR）
4. BIS 交叉管控：2024年3月起 §744.8 规定 SDN 自动触发 EAR 对**所有物项**的许可要求

> "BIS implements additional EAR license requirements for all items subject to the EAR for all persons blocked under specified OFAC-administered sanctions programs."

— *89 FR 20107, Mar 21, 2024*

**2025年9月 Affiliates Rule 扩展**：

BIS 引入与 OFAC 对等的 50% 所有权规则：Entity List/MEU List/SDN 实体的 ≥50% 子公司自动受限，适用最严格规则。

> "An entity owned 50 percent or more... by multiple entities subject to EAR license requirements pursuant to some combination of the Entity List, MEU List, or SDN List... is subject to the most restrictive license requirements."

— *Federal Register, Sep 30, 2025*

**典型对象**：俄罗斯特定寡头/银行/军工企业、中国特定个人/实体（涉疆、涉港、涉军 SDN）、恐怖主义相关实体。

**影响**：彻底切断美元体系和美国市场。全球合规风险极高，国际银行拒绝服务。

---

### T2: 华为级 — Entity List + FN1 FDP + Presumption of Denial

美国商务管制体系内**最严厉的单实体制裁**。华为是唯一 FN1 实体。

**制裁时间线**：

- **2019年5月16日** — 华为 + 68 家非美国关联公司列入 Entity List。许可审查：**Presumption of denial for ALL items subject to the EAR**（84 FR 22961）
- **2019年8月19日** — 再加 46 家关联公司（84 FR 43487），累计 114 家
- **2020年8月** — 再加 38 家 + 撤销临时通用许可 (TGL) + 施加 **Footnote 1 FDP 规则**（85 FR 51563）

> "Huawei Technologies Co., Ltd., Shenzhen, China. \| For all items subject to the EAR. (See §744.11 of the EAR). \| **Presumption of denial**"

— *Entity List, 84 FR 22961*

**FN1 FDP 规则（华为独有）**：

任何国家生产的任何产品，只要是特定美国软件/技术的"直接产品"且交易涉及华为，**自动受 EAR 管辖**。这是长臂管辖的极致——第三方国家的第三方产品也要追溯审查。

**实际效果**：

- 全球任何国家生产的芯片，只要用了美国技术且流向华为 → 自动受美国出口管制
- Google 断供 GMS → 海外手机市场归零
- 台积电断供 → 麒麟芯片停摆
- 自研芯片只能靠中芯国际 DUV 多重曝光（良率 20-40%，台积电 7nm 良率 >90%）
- 被迫转向鸿蒙 + 自研 EDA + 国产供应链

---

### T3: SMIC 级 — Entity List + FN5 FDP + 先进制程推定拒绝

比华为低一级：成熟制程可 case-by-case。

**制裁行动**：

| 时间 | 行动 | 来源 |
|------|------|------|
| 2020年12月18日 | 中芯国际列入。10nm 以下推定拒绝，其他逐案审查 | 85 FR 83416 |
| 2024年12月2日 | 全面升级：**140 家实体**加入 + 24 种 SME 设备管控 + HBM 管控 + **FN5 FDP 规则** | BIS Press Release, Dec 2, 2024 |
| 2025年9月16日 | 新增 **32 家实体**（中国 23 家 + 新加坡/印度/台湾/土耳其/UAE 9 家） | Federal Register, Sep 16, 2025 |

**列入理由**（2020年原文）：

> "Specifically, these entities acquired U.S. origin semiconductor manufacturing equipment for two Entity List parties... without the requisite license or authorization from BIS."

— *85 FR 83416, Dec 22, 2020*

**2024年12月升级理由**（BIS 官方声明）：

> "Commerce Strengthens Export Controls to Restrict China's Capability to Produce Advanced Semiconductors for Military Applications... The purpose is to stop PRC companies from leveraging U.S. technology to indigenously produce advanced semiconductors."

— *BIS Press Release, Dec 2, 2024 (Secretary Raimondo, NSA Sullivan, Under Secretary Estevez)*

**FN5 FDP 规则**：任何外国生产的半导体制造设备，如已知涉及 FN5 实体参与，受 EAR 管辖。

**SME FDP 规则**：外国生产的 SME，如已知目的地是 D:5 国家（含中国），受 EAR 管辖。

**140 家新增实体分类（2024年12月）**：

- 半导体晶圆厂 (semiconductor fabrication facilities)
- 设备制造商 (tool companies)
- 投资公司 (investment companies)
- 涵盖中国、新加坡、韩国等司法辖区

**影响**：

- EUV 光刻机完全无法购买 → 5nm 以下无法实现
- 先进 DUV (NXT:2050i/2100i) 出口许可推定拒绝
- 7nm 只能靠存量 DUV + 多重曝光，良率 20-40%
- 第三方国家（新加坡、马来西亚）生产设备也受管辖

**典型 FN5 对象**：芯恩、鹏新旭、昇维旭、部分设备公司。

---

### T4: 标准 Entity List — Presumption of Denial

列入 Entity List，许可审查为全部推定拒绝，但**无特殊 FDP 规则**（受 50% Affiliates Rule 自动扩展）。

**中国典型对象**：

| 企业 | 列入时间 |
|------|----------|
| 海光信息 (Hygon) | 2019年6月 |
| 寒武纪 (Cambricon) | 2022年12月 |
| 景嘉微 (Jingjia Micro) | 2021年12月 |
| 上海微电子 (SMEE) | 2022年12月 |
| 南大光电 (Nata Opto) + 7家子公司 | 2024年12月 |
| 壁仞科技 (Biren) · 摩尔线程 (Moore Threads) | 2023年10月 |
| 地平线 (Horizon Robotics) | 2023年 |

**影响**：

- 无法从美国及盟友直接购买芯片/IP/软件
- 无法使用台积电、三星先进制程代工
- 无法获取 Cadence/Synopsys 先进 EDA
- 可通过国内供应链 + 成熟制程代工 + 自主研发部分绕过

---

### T5: Entity List — Case-by-Case Review

逐案审查。理论上可能获批，需证明不危害美国国家安全。商用/民用产品限制相对宽松。

---

### T6: Military End-User (MEU) List

法律依据：15 CFR §744.21, Supplement No. 7 to Part 744。

仅对**特定与军事最终用途相关的物项**施加许可要求，不如 Entity List 全面。2025年9月起 Affiliates Rule 适用：MEU 实体 ≥50% 子公司自动受限。

---

### T7: Unverified List (UVL)

法律依据：15 CFR §744.15, Supplement No. 6。

BIS 无法完成最终用途核查时列入。**不推定拒绝**— 无 License Exception + 额外声明要求。Affiliates Rule **不适用**于 UVL。

> "BIS is not adopting the Affiliates rule at this time for... the Unverified List (UVL)."

— *Federal Register, Sep 30, 2025*

---

### T8: 产品/目的地管控 — Advanced Computing & SME Controls

不是对实体的制裁，而是对**产品和目的地**的管控。

**法律依据**：Oct 7, 2022 IFR → Oct 25, 2023 SME IFR → Dec 2, 2024 升级

> "Due to the significance of semiconductors... PRC political and scientific leaders have sought to develop an 'independent and controllable' semiconductor industry."

— *Federal Register, Dec 5, 2024*

**管控范围**：

- ECCN 3A090 先进计算 IC → D:5 国家推定拒绝
- 24 种半导体制造设备 → D:5 + Macau 管控
- HBM 管控 → License Exception HBM
- ECAD/TCAD 软件 → advanced-node IC 设计管控
- SME FDP 规则：已知目的地是 D:5，外国生产 SME 受 EAR 管辖

BIS 将此策略称为 "small yard, high fence"。

**关键时间节点**：

- **2022年10月7日** — 首次先进计算管控 IFR，引入 FN4 FDP
- **2023年10月25日** — SME IFR，扩展设备管控
- **2024年12月2日** — 24 种 SME + HBM + 140 家实体 + FN5 FDP + SME FDP

---

## 四、横向对比

| 等级 | 制裁工具 | 许可政策 | FDP | 资产冻结 | Affiliates | 典型对象 | 主要法律文号 |
|------|----------|----------|-----|----------|------------|----------|-------------|
| **T0** | OFAC 全面禁运 | 无 | — | ✅ | — | 伊朗/朝鲜/叙利亚/古巴 | 31 CFR 500s |
| **T1** | OFAC SDN | 极少 | — | ✅ | ✅ 50% | 特定个人/实体 | 31 CFR Ch. V |
| **T2** | EL + FN1 FDP | 全部推定拒绝 | ✅ FN1 | — | ✅ 50% | 华为(唯一) | 84 FR 22961 等 |
| **T3** | EL + FN5 FDP | 先进推定拒绝 | ✅ FN5/SME | — | ✅ 50% | SMIC/芯恩等 | 85 FR 83416; Dec 2024 |
| **T4** | EL Presumption | 推定拒绝 | — | — | ✅ 50% | 寒武纪/壁仞/海光 | 各批次 FR |
| **T5** | EL Case-by-Case | 逐案 | — | — | ✅ 50% | 非核心实体 | 各批次 FR |
| **T6** | MEU List | 特定物项 | — | — | ✅ 50% | 军工关联实体 | §744.21 |
| **T7** | UVL | 不拒绝 | — | — | ❌ | 待核查实体 | §744.15 |
| **T8** | 产品管控 | 推定拒绝 | ✅ SME FDP | — | — | 全 D:5 目的地 | Dec 2024 IFR |

---

## 五、案例对比：华为 T2 vs 摩尔线程 T4

同样在 Entity List 上，差距巨大。本质区别不在"是否被列入"，而在**被列入之后叠加了什么规则**。

| 维度 | 华为 (T2) | 摩尔线程 (T4) |
|------|-----------|---------------|
| 列入时间 | 2019年5月 | 2023年10月 |
| 许可审查 | Presumption of denial | Presumption of denial |
| FDP 规则 | **✅ FN1 — 全球任何国家生产的任何产品** | **❌ 无** |
| 打击范围 | 150+ 关联公司全部列名 | 仅本实体（受 Affiliates Rule） |
| 临时许可 | 有 TGL 阶段，2020年撤销 | 无 TGL，直接列入 |
| 独特性 | **唯一 FN1 实体** | 普通 Entity List 成员 |

**FN1 的本质区别**：

华为的 FN1 FDP 规则是独一份的规定——**任何一个国家（新加坡、马来西亚、以色列）生产的芯片，只要是美国软件/技术的"直接产品"且最终流向华为，就自动受美国出口管制**。这是长臂管辖的极致。

摩尔线程可以走国内渠道拿到代工产能，只是不能直接从美国/台积电/三星拿货。华为是连第三方国家的第三方产品都被追溯拦截。两者虽然同在 Entity List，实际差距至少两级。

---

## 六、结语：制裁的工具组合逻辑

理解美国制裁体系的关键不在于记住每个层级的细节，而在于理解**工具组合的递进逻辑**：

1. **T0-T1：铁幕** — 用 OFAC 的金融铁幕，对国家和个人实现完全金融隔绝。一刀切，不留余地。
2. **T2-T3：手术刀** — 用 BIS 的 FDP 规则，对特定实体实现技术长臂管辖。精准打击技术能力而非金融资产。
3. **T4-T7：梯度网** — 用不同程度的许可证政策（推定拒绝 → 逐案审查 → 特定物项 → 待核查），对大批实体实施梯度管控。
4. **T8：围墙** — 用产品/目的地管控，对整个行业划定"禁区"。不是制裁实体，而是管制品类。

**这四种工具不是替代关系，是叠加关系。** 同一个实体可能同时承受多种制裁工具。制裁体系的核心能力在于：美国可以根据威胁程度，自由组合这些工具，精确调控打击力度。

而 FN1 FDP 这种独一份的规则，说明了一件事：当某个实体被认为具有**系统性威胁**时，美国愿意为其单独设计一套法律工具——绕过国际供应链、第三方国家、甚至物理距离。这不是制裁的常规操作，这是制裁体系的最大功率输出。

---

*本文基于 BIS Federal Register、EAR Part 744/746、OFAC 法规原文整理。分析时间为 2026年8月，法规持续更新中。*
