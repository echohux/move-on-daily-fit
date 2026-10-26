# MOVE ON · Daily Fitness Check-in

> 用每日计划与即时反馈降低健身习惯的启动成本。

![Next.js](https://img.shields.io/badge/Next.js-0F766E?style=flat-square) ![React](https://img.shields.io/badge/React-0F766E?style=flat-square) ![TypeScript](https://img.shields.io/badge/TypeScript-0F766E?style=flat-square)

**在线体验：** [打开产品](https://echohux.github.io/move-on-daily-fit/) · [验收与迭代记录](./docs/EVALUATION.md)

![MOVE ON · Daily Fitness Check-in 项目封面](./docs/assets/readme-cover.svg)

## 项目简介

无需注册的轻量健身打卡产品。根据用户目标、经验与器械条件展示个性化计划，以每日完成进度、连续打卡和年度活动日历帮助用户观察习惯变化。

项目重点解决以下问题：

- 开始困难：先给出可执行的每日任务，再展示完成反馈。
- 进步不可见：用连续记录、累计时长和活动日历展示投入。
- 隐私顾虑：个人资料和打卡记录保留在当前浏览器。

## 核心能力

- 根据目标、经验和器械条件匹配训练计划。
- 每日动作列表与完成进度。
- 一键打卡、连续天数与累计训练时间。
- 最多 365 天历史活动日历。
- 适配移动端与桌面端的展示。

## 产品流程 · Pipeline

```text
填写目标、经验与器械条件
    ↓
匹配计划 → 查看当天动作
    ↓
完成训练 → 更新进度 → 打卡
    ↓
保存到 localStorage
    ↓
查看连续记录、时长与活动日历
    ↓
按后续目标调整资料与计划
```

这是以计划逻辑和本地记录为核心的健身习惯产品。当前公开说明与源码未证明存在模型推理、实时动作识别或 AI 教练 Agent。

## 评测闭环

将核心任务、状态反馈与稳定性分开验收，再保留失败样例进行回归：

| 层级 | 验收关注点 |
| --- | --- |
| 结果质量 | 核心流程是否完成，输出或记录是否符合输入 |
| 过程质量 | 必要状态、异常反馈、数据一致性与可恢复性 |
| 稳定性 | 刷新与重复操作、依赖故障、存储或发布边界 |

```text
体验核心流程 → 记录实际结果 → 标注 Good / Bad / Boundary Case
      ↑                                      ↓
回归同一组用例 ← 修复并对比结果 ← 定位规则 / 数据 / 交互 / 依赖原因
```

这是本次补充的验收与迭代规范，尚未代表已经完成评测、建立自动化平台或取得量化成绩。项目专属用例与待填写记录见 [EVALUATION.md](./docs/EVALUATION.md)。

## 技术架构

- 公开站点：`docs/`，包含可直接部署的静态产物。
- 源码：`move-on-daily-fit-source.zip` 内的 `app/page.tsx`、布局与样式。
- 核心业务记录：浏览器 localStorage。
- 源码依赖包含 Next.js、React、TypeScript、Tailwind，以及 Vinext / Vite 构建配置。

**技术栈：** Next.js · React · TypeScript · Tailwind CSS · localStorage。

## 本地运行

只预览公开静态站点：

```bash
python3 -m http.server 8080 --directory docs
```

打开 `http://localhost:8080/`。源码请下载并解压 [源码包](./move-on-daily-fit-source.zip)。源码包要求 Node.js 22.13+，其 `package.json` 提供 pnpm 开发、构建和测试命令；但 `vite.config.ts` 引用了包内未附带的 `.openai/hosting.json`，因此现有源码包并非完整开箱即用的开发环境，需先补齐对应宿主配置或调整构建方案。

## 部署

现有 Pages workflow 直接上传 `docs/`，由 `main` 分支的 `docs/**` 或 workflow 改动触发。源码 ZIP 不会被此 workflow 自动编译；修改应用源码后需要重新生成静态产物并更新 `docs/`。

## 项目结构

```text
docs/                           # GitHub Pages 静态产物
move-on-daily-fit-source.zip     # 源码归档
.github/workflows/              # 上传 docs 的 Pages 任务
docs/EVALUATION.md              # 验收用例与记录规范
```

## 产品取舍与边界

清除浏览器存储会删除资料和训练记录，没有账号同步能力。训练计划是一般健身产品功能，不等于个体医疗判断。源码归档存在宿主配置依赖，开发复现状态需单独验证。

## 项目背景

项目通过 Vibe Coding 构建，产品关注点包括需求定义、任务流程、交互优先级与快速验证。本次说明文档参考 [FlowCraft AI](https://github.com/FILPPED-jin/FlowCraft-AI-Product) 的项目展示结构，按本仓库实际内容重新组织。
