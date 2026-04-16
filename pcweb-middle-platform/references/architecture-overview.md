# 架构概览

PC Web 架构遵循分层、模块化、标准化和工程化设计。

## 分层

- UI 层：React 页面和组件、AntD UI、路由、交互、PC 布局。
- 业务逻辑层：页面编排、校验、事件处理、自定义 hooks。
- 数据层：API services、请求封装、本地缓存、已有共享应用状态。
- 工具层：通用函数、常量、配置、鉴权辅助函数、格式化工具。
- 工程层：Vite 构建、ESLint、TypeScript、部署、环境配置。

## 设计原则

- 清晰的职责边界。
- 高内聚、低耦合。
- 通过共享组件、hooks、services 和工具函数实现复用。
- 为业务数据、API 数据、组件 props 和工具函数契约提供类型安全。
- 企业级 PC UI 优先使用 AntD。
- 在模板支持的范围内使用配置驱动布局和主题。
- 在路由、菜单、按钮和数据显示层面进行安全与权限检查，并以后端作为最终权威。

## 结合模板理解

白皮书描述的是目标能力，但模板才是实现层面的事实来源。例如：

- 使用已安装的 React/Vite/Router 版本，而不是白皮书里命名的旧版本。
- 如果当前模块可以用现有 hooks 和本地状态处理，不要添加 Redux。
- 除非项目已经采用 Less 或用户要求迁移，否则不要把 CSS 迁移到 Less。
- 不要在无关功能开发中顺手添加 Jest 或测试基础设施。

## 期望的模块形态

一个结构良好的业务模块通常包括：

- `src/pages/<module>/index.tsx` 中的页面入口
- `src/pages/<module>/components` 下的局部组件
- `src/pages/<module>/hooks` 下的局部 hooks
- `src/services/<module>.ts` 下带类型的 service 函数
- 仅当跨模块复用时，在 `src/types/<module>.ts` 放置共享类型
- `src/router/routeConfig.tsx` 中的路由元数据
