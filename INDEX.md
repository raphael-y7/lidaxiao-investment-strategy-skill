# Skill 地图 — 李大霄投资战略（第三版）

本文件由 `bundle/verified.yaml` 生成：10 张能力卡按"先过闸门、再定位、再算账、最后落到买什么与情绪自检"排成一张可路由的地图，路由入口先接住问题，再按意图加载 1–2 张卡。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| ldxx-position-posture | position-posture | 大势位置—操作姿态总纲 | 5 星 | router → 路由入口 |
| ldxx-bottom-identification-skill | bottom-identification-skill | 历史大底五维识别 | 5 星 | promoted → 独立 skill |
| ldxx-top-bubble-signals-skill | top-bubble-signals-skill | 顶部、泡沫与转弱信号识别 | 5 星 | promoted → 独立 skill |
| ldxx-wind-vane-tracking-skill | wind-vane-tracking-skill | 风向标与跨市场资金跟踪 | 5 星 | promoted → 独立 skill |
| ldxx-bond-stock-spread-skill | bond-stock-spread-skill | 股债差逆向配置与高息牛判别 | 5 星 | promoted → 独立 skill |
| ldxx-fund-flow-policy-skill | fund-flow-policy-skill | 资金供需流量与政策研判 | 4 星 | promoted → 独立 skill |
| ldxx-entry-qualification | entry-qualification | 入市资格自检与散户进阶 | 4 星 | router → 路由入口 |
| ldxx-strategy-fit | strategy-fit | 策略定位与能力自检 | 4 星 | router → 路由入口 |
| ldxx-stock-selection-skill | stock-selection-skill | 选股优先与排除 | 5 星 | promoted → 独立 skill |
| ldxx-sentiment-contrarian | sentiment-contrarian | 情绪逆向与信息甄别 | 4 星 | router → 路由入口 |

合计 10 张：promoted 6 张（在 `pack/` 里各自独立成 skill）、router 4 张（留在路由入口的 `references/capabilities/` 里由路由表分流）。每张卡的正文在 `bundle/cards/ldxx-<slug>.md`，同一份内容另以 `references/capabilities/<slug>.md` 出现在 `single/` 与 `pack/*-router/` 中。

## 依赖关系

`bundle/verified.yaml` 的 `also_read` 字段记录"读完这张卡之后还该补哪张"，共 10 条，全部指向同书能力卡：

| 能力卡（capability_id） | also_read（补读） |
|---|---|
| ldxx-position-posture | ldxx-bottom-identification-skill、ldxx-top-bubble-signals-skill |
| ldxx-bottom-identification-skill | ldxx-position-posture、ldxx-wind-vane-tracking-skill、ldxx-bond-stock-spread-skill、ldxx-sentiment-contrarian |
| ldxx-top-bubble-signals-skill | ldxx-position-posture、ldxx-bond-stock-spread-skill、ldxx-sentiment-contrarian |
| ldxx-wind-vane-tracking-skill | ldxx-bottom-identification-skill、ldxx-top-bubble-signals-skill、ldxx-fund-flow-policy-skill |
| ldxx-bond-stock-spread-skill | ldxx-bottom-identification-skill、ldxx-top-bubble-signals-skill、ldxx-fund-flow-policy-skill |
| ldxx-fund-flow-policy-skill | ldxx-wind-vane-tracking-skill、ldxx-bond-stock-spread-skill |
| ldxx-entry-qualification | ldxx-strategy-fit、ldxx-stock-selection-skill |
| ldxx-strategy-fit | ldxx-entry-qualification、ldxx-stock-selection-skill |
| ldxx-stock-selection-skill | ldxx-strategy-fit、ldxx-entry-qualification、ldxx-bottom-identification-skill |
| ldxx-sentiment-contrarian | ldxx-bottom-identification-skill、ldxx-top-bubble-signals-skill |

按被补读次数排序，网络的中心是两张判定卡：`ldxx-bottom-identification-skill`（被 5 张卡列为补读）与 `ldxx-top-bubble-signals-skill`（被 4 张卡列为补读），其次是 `ldxx-bond-stock-spread-skill`（3 次）。`ldxx-position-posture` 与 `ldxx-wind-vane-tracking-skill` 各被补读 2 次。

## 加载顺序

1. **先读入口 SKILL.md**。single 模式读 `single/lidaxiao-investment-strategy-skill/SKILL.md`；pack 模式读 `pack/lidaxiao-investment-strategy-skill-router/SKILL.md`。入口给的是触发条件、核心原则（常驻速览）与意图路由表。
2. **按路由表加载 1 张能力卡**，任务明确跨域时最多加载 2 张。不要在入口处就把 10 张卡全塞进上下文。
3. **再按 also_read 补读**。只有当前卡把结论明确交给另一张卡时才补读（例如底部判定成立后交给 `ldxx-position-posture` 谈操作姿态），不构成"读完一张就要读全部邻居"。
4. **概览、书名、术语类问题不加载能力卡**，直接用入口的核心原则加 `references/overview.md`、`references/glossary.md` 回答；决策规则速查用 `references/cheatsheet.md`。
5. **路由表与 capability-index 都命中不了**的意图，直接告知超出本书范围，不硬套卡片。
