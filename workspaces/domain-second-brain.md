# 领域第二大脑

## 契约

### 目标

领域第二大脑是领域内的一个工作区：以[章程](../../../../../assets/quanttide-bylaw/domains/meta/memory/second-brain.md)定义的资产类型为骨架存放领域知识，使各领域结构一致、可互相引用。

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

目录名与章程的资产类型一一对应，各资产独立成仓、父仓库只追踪引用。Context 是默认入口，Archive 是过时资产的出口；产出按流动规则转出到目标领域的对应资产，不在上游留副本。新建领域第二大脑时登记到本文件目录。

### 验收

- 目录集合与章程的资产类型对得上：data/ 十一件、docs/ 六件，另有工具箱、平台、实验室。
- 每件资产是独立仓库，父仓库只追踪引用，不直接改子仓库文件。
- 默认入口与备份出口齐备：context/ 与 archive/。
- 与已建成的领域第二大脑并排比对，结构一致——跨领域因此可关联分析。
- 新建的领域第二大脑已登记到目录。

## 目录

- 学术研究（quanttide-academics）
- 智能体工程（quanttide-agent）
- 数字资产管理（quanttide-asset）
- 身份认证（quanttide-auth）
- 商务拓展（quanttide-business）
- 软件工程（quanttide-code）
- 沟通管理（quanttide-connect）
- 课程（quanttide-course）
- 众包管理（quanttide-crowd）
- 客户关系管理（quanttide-customer）
- 数据工程（quanttide-data）
- 议事管理（quanttide-delib）
- 交互设计（quanttide-design）
- DevOps（quanttide-devops）
- 文档工程（quanttide-docs）
- 经济建模（quanttide-econ）
- 创业管理（quanttide-entrep）
- 执行管理（quanttide-execute）
- 金融（quanttide-finance）
- 增长管理（quanttide-growth）
- 健康管理（quanttide-health）
- 人力资源（quanttide-human）
- 创新管理（quanttide-innov）
- 知识工程（quanttide-knowl）
- 学习管理（quanttide-learn）
- 新媒体运营（quanttide-media）
- 元工程（quanttide-meta）
- 组织管理（quanttide-org）
- 支付工程（quanttide-pay）
- 产品研发（quanttide-product）
- 项目管理（quanttide-project）
- 销售管理（quanttide-sales）
- 机密管理（quanttide-secret）
- 安全工程（quanttide-security）
- 战略管理（quanttide-strategy）
- 客户支持（quanttide-support）
- 认知工程（quanttide-think）
- 知识工作（quanttide-work）——本文件所在领域
- 叙事工程（quanttide-write）
