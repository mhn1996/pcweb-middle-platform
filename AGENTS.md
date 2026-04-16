# 企业级 PC Web Agent 提示词

你正在参与一个企业级 PC Web 中台项目。

以当前仓库作为已实现架构的唯一事实来源。目标技术栈为 React 19、Vite、TypeScript、Ant Design 6、React Router、统一 fetch 封装、CSS/CSS Modules，以及项目级页面/主题配置。不要因为白皮书描述了更完整的目标状态，就替换当前可运行的架构。

## 优先级

当规则之间发生冲突时，按以下顺序执行：

1. 当前模板代码和可运行架构。
2. `guidelines/*.md` 中的实现规则。
3. PC Web 白皮书中的目标状态指导和评审标准。
4. 通用前端最佳实践。

除非用户明确要求迁移，或仓库已经具备对应配置，否则不要引入 Redux、Jest、Husky、Prettier、Less、React Query 或其他尚未集成的系统。

## 硬性规则

- 保持现有路由、鉴权、布局、菜单、主题和请求模式稳定。
- 业务页面优先使用 AntD：在编写自定义 UI 前，优先使用 AntD 组件实现布局、表单、表格、弹窗、抽屉、标签页、反馈、导航和常见企业级交互。
- 不要在 `src/imports/**` 下新增实现；设计稿/Figma 产物必须规范化到正式业务目录中。
- 通过 `src/router/routeConfig.tsx` 新增或修改路由；保持 `ProtectedRoute`、懒加载、角色控制、选中菜单行为和重定向稳定。
- API 调用使用 `src/utils/request.ts` 和 `src/services/**`；除非正在修改请求基础设施本身，否则不要在页面中直接调用原生 `fetch`。
- 为请求、响应、组件 props 和业务数据定义 TypeScript 类型。避免使用 `any`；如果无法避免，需要在本地说明原因。
- 页面私有组件和 hooks 放在页面模块内。只有在跨模块复用时，才提升到全局 `components`、`hooks` 或 `utils`。
- 优先使用 AntD 主题 token、`src/config/pageConfig.json`、CSS 变量和 CSS Modules。避免在页面层堆叠硬编码颜色、间距、字体和圆角。
- 替换页面时，在同一次变更中移除废弃页面实现、过期 imports 和无效引用。
- 保护敏感数据：不要记录 token、密码、患者敏感数据或原始敏感 API 响应。

## 默认工作流程

1. 编辑前阅读相关现有文件：路由配置、目标页面/模块、services、hooks、layout/config，以及 `guidelines/*.md`。
2. 做出最小且兼容当前架构的变更。
3. 保持 UI 结构符合企业级产品习惯：页面头部、筛选/搜索区域、操作区域、内容区域、分页、弹窗/抽屉/表单反馈等按需组织。
4. 条件允许时运行 `npm run lint` 和 `npm run build`。
5. 汇报变更文件、验证结果，以及模板和白皮书之间仍未解决的冲突。
