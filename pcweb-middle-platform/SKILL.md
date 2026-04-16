---
name: pcweb-middle-platform
description: 用于基于 React/Vite/TypeScript/AntD 模板和 PC Web 白皮书实现、评审或初始化企业级 PC Web 中台项目。覆盖业务页面、Figma 转代码清理、路由、API 集成、样式 token、质量评审和项目搭建。
---

# PC Web 中台

此技能会把 PC Web 白皮书和中台模板转化为可执行的 agent 行为。工作流需要持续参考本文件，其他参考文档按需加载。

## 第一步

编辑代码前，先识别任务类型：

- **业务功能/页面**：阅读 `references/template-map.md`、`references/feature-development.md` 和仓库中的 `guidelines/*.md`。
- **Figma/设计稿转代码**：阅读 `references/figma-to-code.md`、`references/style-and-token.md` 和仓库中的 `guidelines/*.md`。
- **API 集成**：阅读 `references/api-and-openapi.md`，并检查 `src/utils/request.ts`、`src/services/**` 和 `src/docs/**`。
- **样式/主题/布局**：阅读 `references/style-and-token.md`，并查看 `src/config/pageConfig.json`。
- **评审/MR 检查**：阅读 `references/review-checklist.md` 和相关领域参考文档。
- **项目初始化**：阅读 `references/bootstrap.md` 和 `references/template-map.md`。

## 核心优先级

当规则冲突时：

1. 以当前模板代码和可运行架构为准。
2. 仓库中的 `guidelines/*.md` 优先于长篇白皮书文本。
3. 白皮书作为目标状态指导和评审知识。
4. 通用前端最佳实践用于补齐空白。

除非用户明确要求迁移，否则不要添加白皮书中提到但项目尚未集成的系统，例如 Redux、Jest、Husky、Prettier、Less 或 React Query。

## 硬性规则

- 保持路由、鉴权守卫、布局、菜单、标签页、面包屑和主题配置稳定。
- 企业级 PC 业务 UI 优先使用 Ant Design。
- 不要在 `src/imports/**` 中创建新的实现。
- 业务路由通过 `src/router/routeConfig.tsx` 注册。
- API 调用使用 `src/utils/request.ts` 和 `src/services/**`。
- 为 props、API 参数、API 响应和业务数据定义 TypeScript 类型。
- 在硬编码视觉值之前，优先使用项目 token/配置。
- 在同一次变更中移除被替换的旧代码和过期 imports。
- 条件允许时运行 lint/build，并清楚报告失败原因。

## 输出要求

完成时总结：

- 改了什么。
- 涉及哪些文件。
- 运行了哪些检查。
- 是否存在模板与白皮书之间的取舍。
