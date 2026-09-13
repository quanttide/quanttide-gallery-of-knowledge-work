# 领域第二大脑

## 契约

### 目标

领域第二大脑是领域内的一个工作区：以[产物类别](../../specification/piece/artifact.md)为骨架存放领域知识，使各领域结构一致、可互相引用（跨领域框架见[章程](../../../../../assets/quanttide-bylaw/domains/meta/memory/second-brain.md)）。

### 一般格式

```text
{domain}/
├── data/                       陈述型九宫格与不占格资产
│   ├── report/ library/ history/      过去：报告、参考、历史
│   ├── journal/ profile/ brochure/    现在：日志、档案、宣传册
│   ├── roadmap/ insight/ intention/   未来：路线图、洞察、意图
│   └── context/ archive/              默认入口与备份出口
├── docs/                       程序型的文档类
│   ├── bylaw/ specification/          宪法：章程、规格
│   ├── handbook/ gallery/             法律：手册、案例
│   └── tutorial/ essay/               法理：教程、札记
├── packages/{domain}-toolkit/  Toolkit：工具箱
├── apps/{app}/                 Platform：平台
└── examples/default/           Example：实验室
```

目录名与[产物类别](../../specification/piece/artifact.md)一一对应，各资产独立成仓、父仓库只追踪引用。Context 是默认入口，Archive 是过时资产的出口；产出按流动规则转出到目标领域的对应资产，不在上游留副本。新建领域第二大脑时登记到本文件目录。

### 验收

- 目录集合与产物类别对得上，另有工具箱、平台、实验室。
- 每件资产是独立仓库，父仓库只追踪引用，不直接改子仓库文件。
- 默认入口与备份出口齐备：context/ 与 archive/。
- 与已建成的领域第二大脑并排比对，结构一致——跨领域因此可关联分析。
- 新建的领域第二大脑已登记到目录。

## 目录

- 量潮学术研究（quanttide-academics）
- 量潮智能体工程（quanttide-agent）
- 量潮数字资产管理（quanttide-asset）
- 量潮身份认证（quanttide-auth）
- 量潮商务拓展（quanttide-business）
- 量潮软件工程（quanttide-code）
- 量潮沟通管理（quanttide-connect）
- 量潮课程研发（quanttide-course）
- 量潮众包管理（quanttide-crowd）
- 量潮客户关系（quanttide-customer）
- 量潮数据工程（quanttide-data）
- 量潮议事管理（quanttide-delib）
- 量潮交互设计（quanttide-design）
- 量潮DevOps工程（quanttide-devops）
- 量潮文档工程（quanttide-docs）
- 量潮经济建模（quanttide-econ）
- 量潮创业管理（quanttide-entrep）
- 量潮执行管理（quanttide-execute）
- 量潮金融（quanttide-finance）
- 量潮增长管理（quanttide-growth）
- 量潮健康管理（quanttide-health）
- 量潮人力资源（quanttide-human）
- 量潮创新管理（quanttide-innov）
- 量潮知识工程（quanttide-knowl）
- 量潮学习管理（quanttide-learn）
- 量潮新媒体运营（quanttide-media）
- 量潮元工程（quanttide-meta）
- 量潮组织管理（quanttide-org）
- 量潮支付工程（quanttide-pay）
- 量潮产品研发（quanttide-product）
- 量潮项目管理（quanttide-project）
- 量潮销售管理（quanttide-sales）
- 量潮机密管理（quanttide-secret）
- 量潮安全工程（quanttide-security）
- 量潮战略管理（quanttide-strategy）
- 量潮客户支持（quanttide-support）
- 量潮认知工程（quanttide-think）
- 量潮知识工作（quanttide-work）——本文件所在领域
- 量潮叙事工程（quanttide-write）
