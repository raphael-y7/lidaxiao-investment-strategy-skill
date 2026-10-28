# Stage 4 压力测试摘要

> 本摘要由阶段 4 的三份逐卡测试报告（`evals/测试报告-A/B/C.md`）与各 skill 目录下的 `test-prompts.json` 汇总而成。只写归档里确实存在的内容，未记录的项目明确标"未记录"。

## 测试范围

- **本包 skill 数**：可安装入口 8 个——single 模式 1 个入口（`lidaxiao-investment-strategy-skill`，内含 10 张能力卡）+ pack 模式 7 个入口（1 个 `lidaxiao-investment-strategy-skill-router` 路由入口 + 6 个晋级 skill）；底层能力卡共 10 张（U1—U10）。
- **test-prompts 文件**：8 份，每个入口 1 份（single 1 + pack 7），共 48 条用例。
- **用例类型覆盖**：
  - `should_trigger` 24 条（每份 3 条）
  - `should_not_trigger` 16 条（每份 2 条，其中至少 1 条是同书兄弟 skill 的跨卡混淆诱饵）
  - `edge_case` 8 条（每份 1 条）
  - `output_case`：0 条——输出侧不是用 JSON 用例验的，而是在逐卡压力测试里用"1 条代表性任务 + 1 条负例/边界"人工执行、对照卡内 E 段完成标准逐项核对。
- **另附**：`evals/trigger-suite.json` 收 10 条盲测触发用例（trigger 3 条 / no_trigger 7 条）。
- **卡片覆盖**：报告 A 覆盖 U1—U3、报告 B 覆盖 U4—U7、报告 C 覆盖 U8—U10，10 张卡全覆盖。

## 结构检查

- **JSON 可解析性**：仓库内 20 个 JSON 文件全部可解析（含 8 份 `test-prompts.json`、`evals/trigger-suite.json`、`bundle/verified.yaml` 之外的各清单文件），无语法错误。
- **frontmatter**：8 个 `SKILL.md` 全部带 YAML frontmatter，`name` / `description` / `metadata` 三个字段齐全，且 `name` 与所在目录名一致。
- **六段完整性**：`bundle/cards/` 下 10 张能力卡 R / I / A1 / A2 / E / B 六段齐全（10 / 10）。
- **用例内部一致性**：8 份 `test-prompts.json` 的 `skill` 字段与所在目录名逐一对应；每份都是 3 + 2 + 1 结构，`minimum_pass_rate` 均为 0.8，`darwin_compatible` 均为 true。
- **已知不一致（如实登记）**：报告 C 指出 `strategy-fit` 与 `sentiment-contrarian` 的 `keywords` 字面不可达（只能靠语义路由命中），属待回填项，不影响 JSON 结构有效性。

## 结果

- skills: 8 个入口（1 single + 7 pack）/ 10 张能力卡
- test_json: 8
- 通过情况：阶段 4 逐卡压力测试 **10 / 10 PASS**（报告 A 3/3、B 4/4、C 3/3），无 fail 卡片；过程中登记的回填级修正已并入卡片。
- 但必须说明口径：这 10/10 是**人工纸面走查**（测试员模拟能力卡执行者，缺数据一律按判停规则标"无数据"），不是机器跑分。报告 C 明确记载为 fallback 自测、无独立盲测 sub-agent 交叉。机器评测脚本（`run_trigger_evals.py`、`run_output_evals.py`）在本环境未跑通，因此 **48 条 test-prompts 的实测通过率：未记录**；`trigger-suite.json` 的 10 条盲测用例：未记录执行结果。

## 可接入 darwin-skill 的后续动作

- 这 8 份 `test-prompts.json` 已按入口就近放置（`single/<入口>/`、`pack/<skill>/`），`darwin_compatible: true`，可直接作为 darwin-skill 的**回归样本**：每次改卡文、改 `keywords`、改路由表后重跑，`minimum_pass_rate: 0.8` 作为回归门，`should_not_trigger` 要求零容错（诱饵误触发即判失败）。
- `evals/trigger-suite.json` 可作保留集盲测，用来抓"改 A 卡误伤 B 卡"的跨卡回归。
- 接机器判分前建议先补报告 C 的 P8-1 / P10-1 关键词回填，否则字面匹配型评测会把语义可达的用例误判为漏触发。
- 逐卡报告里的完成标准张力和判停输出格式问题（见各报告"回炉修复建议清单"）建议一并回填，再建立机械判分基线。
