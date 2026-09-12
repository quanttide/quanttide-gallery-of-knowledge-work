# 学习任务创建

## 目标

把一份学习任务书从个人档案送出去——先提交到 learn 的 profile（学习管理档案），再提交到 qtclass 仓的 site（量潮课堂站点内容），最后给 site 发一个新版本（推 `site/*` tag，触发 `deploy-site` 构建上传）。

跨三个仓，工作区根是领域仓（`quanttide-work`）：learn 的档案与 qtclass 用相对路径 `../quanttide-learn/data/profile` 与 `../qtclass`；qtclass 需先在本地有工作副本（没克隆就先 `git clone https://github.com/quanttide/qtclass.git ../qtclass`）。发版走 `qtcloud-devops release audit` / `publish`。

**版本号一处都不能落**：`src/site/package.json`、`src/site/CHANGELOG.md`、这条定义判据里写的 tag，三处同时改。

## 步骤与验收

### profile 进学习档案

把任务书落到学习管理档案 `../quanttide-learn/data/profile`（仓 quanttide-profile-of-learning-management，按 learners / schedules / tasks 分）的 `tasks/try-qtcloud-work-cli.md`——本流程实例就用这个名字，定了别再改，站点那边要逐字对上；头里必须带 `title` / `description`（站点靠这两样显示标题与摘要，缺了不进列表），在那边提交推送。提交信息与文件路径抄进报告的「档案」一节。

验收：程序查 `../quanttide-learn/data/profile/tasks/try-qtcloud-work-cli.md` 在、那边工作区干净（改动已提交）、报告里有「## 档案」；智能体审分类对（学习任务归 `tasks`）、内容与源文件一致、提交信息说清了这是哪份任务书。

### site 进课堂站点

站点的学习内容在 `../qtclass/src/site/src/data/learning/` 下按 prices / schedules / tasks 分目录，是档案里对应目录的**逐字副本**（那边怎么放，这边照着放）；把任务书复制到 `src/site/src/data/learning/tasks/try-qtcloud-work-cli.md`，在 qtclass 仓提交推送；落点路径与提交信息抄进报告的「站点」一节。

验收：程序查站点那份与档案那份逐字相同（`diff -q`）、站点这份在 qtclass 仓里被跟踪、那边工作区干净、报告里有「## 站点」；智能体审落点照了 site 既有惯例（不是随便找个目录塞）、站点里链得到。

### audit 发布预检

按档位推进版本（`../qtclass/src/site/package.json` 现为 `0.1.2-beta.6`，beta 内递增，如 `0.1.2-beta.7`），在 `../qtclass/src/site/CHANGELOG.md` 写一节这次变更（任务书上线），两处版本对齐；再 `cd ../qtclass && qtcloud-devops release audit -v site/v0.1.2-beta.7` 预检到 7/7，逐项输出抄进报告的「预检」一节。

预检只在发布前那一刻成立——发布后 tag 已存在、工作区也可能被后续改动扰动，重跑必然报错，所以判据只卡「版本两处对齐」与「工作区干净」两项，预检本身以那一刻的输出为准。

验收：程序查站点版本与变更记录两处对齐、qtclass 那边工作区干净、报告里有「## 预检」；人拍创始人放行（版本号与内容都对过）。

### publish 真发

`cd ../qtclass && qtcloud-devops release publish -y -v site/v0.1.2-beta.7`——它建 tag 推远端，`deploy-site` 工作流随之构建静态站、上传 OSS 桶 `qtclass-site` 并刷 CDN。新 tag 在远端、`deploy-site` 跑绿、站点上查得到这份任务书；三样抄进报告的「发布」一节。

验收：程序查 `site/*0.1.2-beta.7` tag 已在远端、报告里有「## 发布」；智能体审新 tag 与这次内容对应（不是旧 tag 充数）、`deploy-site` 跑绿、站点上查得到这份任务书。

### conclude 收口

写「结论」一节——开头三行（送出去的是什么 / 现在停在哪一步 / 还差什么），随后列仍拿不准的（例如 site 的分类要不要另起一节、任务书要不要按学期归档）。

验收：程序查报告里有「## 结论」；智能体审三行说得清送到了哪、还差什么，拿不准的单列、不混在结论里。

## 产物

本任务的报告，五节：档案 / 站点 / 预检 / 发布 / 结论；外加 learn 档案仓与 qtclass 仓各一次提交，以及一个新的 `site/*` tag。

## 怎么跑

```bash
qtcloud-work task --new learn-task-create --workflow learn-task-create
```

再 `qtcloud-work task learn-task-create --next`，一条一条走。
