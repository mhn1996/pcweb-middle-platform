# 功能开发

用于新增或修改 PC Web 业务模块的工作流。

## 发现阶段

编辑前检查：

- `src/router/routeConfig.tsx`
- 目标 `src/pages/**`
- 相关 `src/services/**`
- 相关 `src/hooks/**`
- 如果涉及布局行为，检查 `src/layouts/index.tsx`
- 如果涉及主题/布局/菜单行为，检查 `src/config/pageConfig.json`
- `guidelines/setup.md`
- `guidelines/components.md`
- `guidelines/styles.md`
- `guidelines/tokens.md`

## 实现规则

- 业务页面放在 `src/pages/<businessModule>/` 下。
- 页面入口使用 `index.tsx`。
- React 组件文件使用 PascalCase。
- hooks 使用 `useXxx.ts`。
- 页面私有组件/hooks 放在页面文件夹内。
- 只有跨模块复用时，才提升到全局共享目录。
- 组件保持聚焦。当页面难以快速浏览时，将大型页面区块拆成局部组件。
- 使用函数组件和 hooks。
- 保持 hook 依赖数组正确。
- 避免不必要的全局状态。局部 UI 使用本地状态；共享应用行为使用项目已有的状态/配置模式。

## 路由规则

- 只在 `src/router/routeConfig.tsx` 中新增或更新路由元数据。
- 按现有路由配置方式一致地懒加载页面组件。
- 保持 `allowedRoles`、`showInMenu`、labels、selected key 行为、重定向和菜单分组稳定。
- 不要绕过 `ProtectedRoute`。
- 不要路由到原始 Figma 导出或 `src/imports/**`。

## UI 规则

- 企业级 PC 交互优先使用 AntD。
- 优先使用 `Layout`、`Flex`、`Space`、`Card`、`Table`、`Form`、`Input`、`Select`、`DatePicker`、`Switch`、`Checkbox`、`Tabs`、`Breadcrumb`、`Dropdown`、`Modal`、`Drawer`、`message`、`notification`、`Result` 和 `Spin`。
- 使用企业用户熟悉的页面结构：标题/页头、筛选、操作、数据区域、分页、批量操作、空/加载/错误状态。
- 避免为单个页面创建一套自定义视觉系统。
- 当 AntD 组件可以表达意图时，避免大段原始 `div` 树。

## 数据规则

- API 函数放在 `src/services/<module>.ts`。
- 使用现有请求封装。
- 定义请求参数和响应数据类型。
- 当后端结构与视图结构不同时，区分 UI 展示类型和 API 类型。
- 在 services 或 hooks 中规范化数据，不要散落在 JSX 中。

## 验证

条件允许时运行：

- `npm run lint`
- `npm run build`

如果检查失败是因为现有项目已经失败，报告第一个相关失败，并说明你的变更是否导致了失败。
