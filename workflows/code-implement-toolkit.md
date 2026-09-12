# 工具箱代码实现

## 目标

把命令行与 studio 里意义相同的领域模型抽到 toolkit。两侧（`apps/qtcloud-work/src/cli` 的 Rust 与 `apps/qtcloud-work/src/studio` 的 Dart）各写了一份同样的模型——信封、执行者、步骤与判据、任务与流水；这份活儿是把它们抽到 `packages/quanttide-work-toolkit`，Rust 与 Dart 各落一份，用同一批用例向量做契约测试，再让两侧依赖已发布的版本号。

**替换完行为一字不改**，尺子为证。

## 步骤与验收

### compare 对比两侧

逐个名词找两侧意义相同的那一份（信封 `Outcome`、执行者与判据种类、工作流定义与步骤、任务与流水、闸门项与产物落点），逐项写出两侧的字段、取值、算法与报错文字，标出「完全相同 / 只差写法 / 只是同名不同义」；再跑一遍尺子，把当前的一致与缺口抄进报告的「对照」一节。输出是一张逐项对照表加抽取范围的建议。

验收：程序查尺子 `apps/qtcloud-work/src/studio/scripts/parity.sh` 跑得起来、报告里有「## 对照」；智能体审表里每一项都两侧点到、都写明是三种里的哪一种并指出各自在哪一行，没有「（待查）」；人拍创始人定抽取范围——哪些进 toolkit，哪些留在各自包里。

### extract 抽进 toolkit

两侧各落一份模型（`packages/quanttide-work-toolkit/packages/rust/` 的 crate `quanttide-work` 与 `packages/quanttide-work-toolkit/packages/dart/` 的包 `quanttide_work`）：字段名、取值、算法与报错文字与原来逐字对齐（抽取不改行为）；测试跟着落，不许留空壳；两个包的清单版本与 CHANGELOG 该动就动。搬了哪些、还留哪些，抄进报告的「抽取」一节。

验收：程序跑两侧门禁——`cd packages/quanttide-work-toolkit/packages/rust && cargo fmt --check && cargo clippy --all-targets -- -D warnings && cargo test --locked`、`cd packages/quanttide-work-toolkit/packages/dart && dart analyze lib/ test/ && dart test`，都要全过，且报告里有「## 抽取」；智能体审两侧同一件事的字段名与取值逐字对齐、测试都不是空壳、报错文字照抄没有顺手改写。

### contract 契约测试

把契约写成**用例向量**——一批 JSON 或 YAML 文件，一对输入与期望输出，两种语言读同一批；写 `packages/quanttide-work-toolkit/scripts/contract.sh`（或同等的两侧入口）跑同一批向量，两侧结论必须一样。向量盖到每个字段与边界：缺字段、多字段、取值不对各给什么。跑一次的输出抄进报告的「契约」一节。

验收：程序跑 `cd packages/quanttide-work-toolkit && sh scripts/contract.sh` 两侧给同一个结论，且报告里有「## 契约」；智能体审向量是两侧共用的同一批文件（不是各写一份测试各说各话）、边界齐、有一处故意写坏的记录证明向量真会红。

### publish-rust 发布 Rust 包

toolkit 的约定是**一个语言包一条发布线**——Rust 与 Dart 各自定版本、各自发，互不牵连（标签形如 `rust/vX.Y.Z-alpha.N`）；把包内 `[Unreleased]` 落成 `## [X.Y.Z-alpha.N]`、清单版本与 `Cargo.lock` 同步（锁文件与版本同一提交，否则发布的 `--locked` 会红）；预检与门禁全过，请创始人放行；`qtcloud-devops release publish -v rust/vX.Y.Z-alpha.N` 建 tag 推远端，`release-rust.yml` 随之发到 crates.io。版本号、tag、发布结果抄进报告的「发布」一节。没有这一步，下一步的替换只能挂本地路径，那不算抽出去。

验收：程序查版本号是这一轮的 `-alpha.N`、清单版本与 CHANGELOG 对得上、`release-rust.yml` 最近一次跑绿、`rust/v*` tag 已在远端、报告里有「## 发布」；智能体审版本是这一轮新落的（不是拿旧版本充数）、包在 crates.io 上查得到；人拍创始人放行（定了版本号就不再改）。

### publish-dart 发布 Dart 包

与 Rust 那条**各发各的**——Dart 的版本号跟自己的改动走，不必与 Rust 对齐（标签形如 `dart/vX.Y.Z-alpha.N`）；同样把 `[Unreleased]` 落成 `## [X.Y.Z-alpha.N]`、清单版本同步；预检与门禁全过，请创始人放行；`qtcloud-devops release publish -v dart/vX.Y.Z-alpha.N` 建 tag，`release-dart.yml` 随之发到 pub.dev（凭证是 `PUBDEV_CREDENTIAL_JSON`，落成 pub 缓存的 `credentials.json`）。

验收：程序查版本号是这一轮的 `-alpha.N`、清单版本与 CHANGELOG 对得上、`release-dart.yml` 最近一次跑绿、`dart/v*` tag 已在远端、报告里有「## 发布」；智能体审版本是这一轮新落的、包在 pub.dev 上查得到；人拍创始人放行。

### adopt 替换到位

两侧删掉自己的同名模型，改成引用**已发布的** toolkit 版本（Rust 写版本号依赖 crates.io，Dart 写版本号依赖 pub.dev；挂本地路径不算抽出去），先编译、再跑各自门禁、再跑尺子——行为一字不改才算过。两侧的依赖改动与删掉的文件清单，抄进报告的「替换」一节。

验收：程序查命令行与 studio 依赖的都是版本号（不是 path）、两侧门禁全过、尺子跑绿、报告里有「## 替换」；智能体审两侧不再留同名模型、抽取过程中没有顺手改行为；人拍创始人确认可以合并（多一层依赖换掉两份重复，值不值）。

### conclude 收口

写报告的「结论」一节——开头三行（抽了什么 / 两侧现在共用到什么程度 / 还差什么），随后列仍拿不准的（例如什么该进 toolkit、什么该留各自包；toolkit 的版本与发版节奏要不要跟两侧对齐）。

验收：程序查报告里有「## 结论」；智能体审三行说得清抽了什么、共用到什么程度、还差什么，拿不准的单列、不混在结论里。

## 产物

本任务的报告，六节：对照 / 抽取 / 契约 / 发布 / 替换 / 结论；外加 toolkit 两个已发布的包与两侧改到版本依赖的清单。

## 怎么跑

```bash
qtcloud-work task --new code-implement-toolkit --workflow code-implement-toolkit
```

再 `qtcloud-work task code-implement-toolkit --next`，一条一条走。
