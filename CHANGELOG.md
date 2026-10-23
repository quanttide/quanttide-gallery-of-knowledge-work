# CHANGELOG

所有显著变更都将记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)。

版本遵循语义化版本规范：0.0.x（探索期）→ 0.x.y（验证期）→ x.y.z（正式期）

---

## [Unreleased]

### 移除

- 产物案例十件迁入[量潮数字资产案例](https://github.com/quanttide/quanttide-gallery-of-asset-management/tree/main/category)：类别归属改为资产类别，标题与首段改为资产口径；本仓 `artifacts/` 目录删除

### 新增

- 流程案例新增「招聘流程」一件：投递邮件 → 候选人清单、评估报告与推荐台账，附同名可运行的 `.yaml`。材料取自 `qtrecurit-private/docs/handbook/workflow.md`（2026-08 按实际运行更新），未编造；每一步带输入、过程、输出与三层验收（程序查 / 智能体审 / 人拍）

---

## [0.1.1] - 2026-09-29

### 变更

- 领域第二大脑与迁移验收改用「产物类别」：不再把类别绑到章程的资产类型表、不再写死件数；类别定义见规格 [产物类别](../specification/piece/artifact.md)
- 案例不再保留旧版——维护直接改到当前版本，删除「旧案不退场」
- 流程案例自 `quanttide-work/data/profile/quanttide/workflows/` 迁入七件（五件按草案整理，两件按工作流定义落成）：代码实现、studio 代码实现、工具箱代码实现、代码重构、设计评审、DevOps 发布、学习任务创建；此后这几条工作流的维护与更新都在本仓
- 可运行的定义（七份 `.yaml`）随案例迁入，与案例同名并列：案例是给人看的正本，YAML 是机器执行的形态
- 流程案例自 `quanttide-work/data/profile/quanttide-founder/workflows/` 再迁入两件：语境到档案、资源落后检测，各附同名可运行的 `.yaml`；此后这两条工作流的维护与更新都在本仓

---

## [0.1.0] - 2026-09-10

### 新增

- 画廊开张：产物案例八件（语境、日志、档案、意图、洞察、规格、手册、路线图），承自 handbook 的具体产物
- 案例索引：产物案例清单与登记规则
- 案例篇：案例的集合载体（登记、维护、累积）
- 流程案例：从意图到路线图，自 handbook/tasks 迁入

### 说明

- 与手册保持同构：目录同名、位置对应，案例可逐条对着规范读
