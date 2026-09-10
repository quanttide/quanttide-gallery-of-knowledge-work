# 领域第二大脑

## 目标

领域第二大脑是领域内的一个工作区：以[章程](../../../../../assets/quanttide-bylaw/domains/meta/memory/second-brain.md)定义的资产类型为骨架存放领域知识，使各领域结构一致、可互相引用。

## 一般格式

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
├── apps/{app}/                 Platform：可部署应用
├── packages/toolkit/           Toolkit：领域共享库
└── examples/default/           Example：实验室
```

目录名与章程的资产类型一一对应，各资产独立成仓、父仓库只追踪引用。Context 是默认入口，Archive 是过时资产的出口；产出按流动规则转出到目标领域的对应资产，不在上游留副本。

## 验收

- 目录集合与章程的资产类型对得上：data/ 十一件、docs/ 六件，另有 apps/、packages/toolkit、examples/default。
- 每件资产是独立仓库，父仓库只追踪引用，不直接改子仓库文件。
- 默认入口与备份出口齐备：context/ 与 archive/。
- 与已建成的领域第二大脑并排比对，结构一致——跨领域因此可关联分析。
