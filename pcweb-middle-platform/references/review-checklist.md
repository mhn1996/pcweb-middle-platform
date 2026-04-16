# 评审清单

用于代码评审或最终交付前检查。

## 架构

- 变更是否遵循现有路由、布局、鉴权、请求、service、hook 和配置模式？
- 是否避免添加不必要的架构或依赖？
- 是否避免新增 `src/imports/**` 实现？
- 替换页面时，旧页面实现、过期 imports 和无效引用是否已移除？

## 路由与权限

- 路由是否注册在 `src/router/routeConfig.tsx`？
- `allowedRoles`、`showInMenu`、labels、icons、菜单分组和选中菜单行为是否正确？
- 必要时页面是否仍在 `ProtectedRoute` 下？
- 未授权操作是否按现有模式隐藏或设门禁？

## UI 与交互

- 业务 UI 是否 AntD First？
- 是否覆盖常见状态：加载、空、错误、成功反馈？
- 表单是否有类型和校验？
- 表格是否按需配置 row keys、columns、pagination/loading？
- 破坏性操作是否有确认？
- 是否尽量通过 AntD 原语保留键盘/可访问性行为？

## TypeScript

- props、service params、service responses 和业务数据是否有类型？
- 是否避免了 `any`？
- 是否处理了 null 和 undefined 情况？
- 需要转换时，API 类型是否与视图模型分离？

## API

- 调用是否集中在 `src/services/**`？
- 代码是否使用 `src/utils/request.ts` 而不是原生 fetch？
- 可用时，是否匹配 OpenAPI 或 `API_INTERFACE_RULES.md`？
- 是否处理分页和标准响应结构？
- 业务错误和网络错误是否清晰处理？

## 样式

- 样式是否优先使用 AntD tokens/config/现有 CSS，而不是硬编码值？
- 页面是否避免多个互相冲突的视觉系统？
- 是否清理了生成式设计样式？
- 布局在常见 PC 宽度下是否稳定？

## 性能

- 适当情况下，重型路由/组件是否懒加载？
- 是否避免重复请求？
- 大型列表是否负责任地处理？
- 监听器、定时器和异步 effects 是否清理？

## 安全

- 日志中是否没有 token、密码和敏感数据？
- 是否避免或净化了用户提供的 HTML？
- 敏感操作是否有确认并有权限检查支撑？
- 前端权限是否被视为 UX 门禁，而不是唯一安全层？

## 验证

- 是否运行了 `npm run lint`？
- 是否运行了 `npm run build`？
- 如果检查失败或跳过，原因是否清楚？
