# 项目初始化

从中台模板创建新项目时使用本参考。

## 初始化目标

- 保持模板架构完整。
- 移除不属于新产品的纯 demo 代码。
- 配置品牌、布局、路由、环境变量和 API base URL。
- 保留鉴权、路由守卫、请求封装和 AntD First 业务 UI 约定。

## 步骤

1. 从批准的模板复制或初始化。
2. 按项目 lockfile 策略安装依赖。
3. 配置产品身份：
   - 必要时配置 `package.json` name
   - 配置 `src/config/pageConfig.json` 中的应用名称、logo、布局、菜单、用户卡片、标签页、面包屑
   - 配置 public logo/assets
4. 配置环境：
   - API base URL
   - 鉴权启用状态
   - 必要时配置部署 base path
5. 清理或替换 demo 路由和 demo 页面。
6. 通过 `src/router/routeConfig.tsx` 添加初始业务路由。
7. 在 `src/services/**` 下添加 service 模块。
8. 不要把 Figma/设计稿代码放在 `src/imports/**`；应规范化到业务页面中。
9. 运行 `npm run lint` 和 `npm run build`。

## 不要自动执行

- 未经请求，不要迁移样式系统。
- 除非项目范围要求，否则不要引入 Redux 或 React Query。
- 除非团队要求落地白皮书中相关章节，否则不要在初始化时添加 Jest/Husky/Prettier 配置。
- 不要因为第一个 demo 页面不需要鉴权，就删除鉴权或路由守卫基础设施。

## 交接检查清单

- 开发服务器可以启动。
- 生产构建成功。
- 默认路由打开真实业务页面或有计划的占位页面。
- 登录/鉴权行为清晰。
- API base URL 可配置。
- Demo imports 和旧页面引用已移除，或说明了保留原因。
