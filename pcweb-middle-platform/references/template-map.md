# 模板地图

在基于中台模板生成的项目中做变更前，先使用这份地图。

## 关键文件

- `package.json`：真实依赖和脚本的事实来源。已检查的模板使用 React 19、Vite 7、TypeScript 5、AntD 6、React Router、基于 Radix 的底层 UI 组件，以及基于 `fetch` 的 services。
- `src/router/routeConfig.tsx`：路由元数据、labels、菜单可见性、icons、角色权限、懒加载页面组件、选中菜单匹配。
- `src/router/index.tsx`：路由渲染、`ProtectedRoute`、布局嵌套、登录路由、默认重定向、404 fallback。
- `src/router/menuUtils.ts`：从路由元数据生成菜单。
- `src/layouts/index.tsx`：主 PC 布局、侧边导航、用户卡片、面包屑、标签页、退出登录流程、页面配置使用。
- `src/config/pageConfig.json`：布局、sider、header、content、logo、菜单、用户卡片、面包屑、页头、标签页、动画、弹窗和类主题项目配置。
- `src/utils/request.ts`：API base URL、鉴权启用状态、token 存储、token 刷新、请求封装、响应解包、错误处理。
- `src/services/**`：按领域分组的类型化业务 API 函数。
- `src/hooks/**`：业务数据编排 hooks。
- `src/docs/openapi_v*.yaml`：可用时作为 API 契约来源。
- `src/docs/API_INTERFACE_RULES.md`：后端/前端 API 结构和命名规则。
- `guidelines/setup.md`：面向 AI 的项目设置和 Figma 转代码红线。
- `guidelines/components.md`：AntD First 组件规则。
- `guidelines/styles.md`：样式系统和布局规则。
- `guidelines/tokens.md`：token 和视觉值决策规则。

## 重要现状说明

- 模板已经具备路由/配置/布局/请求架构。保持它。
- 白皮书提到 React Router 6 和 Vite 5，但模板可能使用更新版本。使用已安装版本。
- 白皮书提到 Less、Redux、Jest、Husky 和 Prettier 作为目标能力。如果项目中不存在，不要自动添加。
- `src/components/ui/**` 可以作为历史底层支持保留，但业务页面不应围绕它重建。
- `src/imports/**` 可能因历史原因存在，但新工作不应通过它接入路由。

## 常见变更位置

- 新页面：`src/pages/<module>/index.tsx`。
- 页面私有组件：`src/pages/<module>/components/<ComponentName>.tsx`。
- 页面私有 hook：`src/pages/<module>/hooks/useXxx.ts`。
- API service：`src/services/<module>.ts`。
- 共享类型：如果跨模块使用，放在 `src/types/<module>.ts`；否则与 service/page 共置。
- 路由入口：`src/router/routeConfig.tsx`。
- 布局/主题配置：`src/config/pageConfig.json`。
