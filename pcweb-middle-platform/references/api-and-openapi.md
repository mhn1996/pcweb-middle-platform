# API 与 OpenAPI

用于 API 集成、service 变更、请求类型定义、OpenAPI 对齐和 API 评审。

## 前端规则

- 使用 `src/utils/request.ts` 作为唯一请求路径。
- 不要在 React 页面或组件中直接调用原生 `fetch`。
- 在 `src/services/<module>.ts` 下新增领域 API 函数。
- 导出 TypeScript 请求和响应类型。
- 优先使用明确的 `Promise<ResponseType>` 签名。
- 注意响应解包行为：模板请求封装可能会直接从 `{ success, data, message, code }` 返回 `data`。
- 端点字符串集中放在 services 中，不要散落在 JSX 里。
- 在 services 或 hooks 中规范化不一致的后端响应结构。
- 实现请求基础设施或长时间运行且绑定组件生命周期的请求时，使用 `AbortController`。

## 后端契约形态

标准响应：

```json
{
  "code": 200,
  "success": true,
  "message": "success",
  "data": {}
}
```

`data` 内的标准分页：

```json
{
  "resultList": [],
  "pageInfoResource": {
    "totalpage": 5,
    "totalsize": 32,
    "pagenum": 2,
    "pagesize": 10
  }
}
```

## 端点约定

- 使用名词和清晰层级。
- 简单查询/读取使用 `GET`。
- 创建、复杂查询和非标准操作使用 `POST`。
- 更新使用 `PUT`。
- 删除使用 `DELETE`。
- 查询条件达到三个或更多时，优先使用携带 body 的 `POST`，避免 URL 过长。
- 除非现有 API 不同，否则分页参数使用 `pageNo` 和 `pageSize`。
- 基础数据或枚举数据优先通过统一的基础数据接口获取（如果可用）。

## 命名

- Service 函数应使用清晰业务名，例如 `getPatientList`、`getPatientDetailById`、`createXxx`、`updateXxx`、`deleteXxx`、`uploadXxx`。
- API 类型在有帮助时应区分 params、DTO、VO 和视图模型：
  - `XxxQueryRequest`
  - `CreateXxxRequest`
  - `UpdateXxxRequest`
  - `XxxVO`
  - `XxxListResponse`

## 错误与安全

- 添加请求层逻辑时，区分业务错误和网络错误。
- 不要记录 token、密码、身份证号、手机号、患者详情或原始敏感响应。
- 刷新失败时，按照现有鉴权行为清除 auth token 并重定向。
- 敏感权限仍必须由后端强制校验；前端路由/按钮权限只是用户体验层面的门禁。

## OpenAPI 工作流

当存在 OpenAPI 文件时：

1. 检查 `src/docs/openapi_v*.yaml`。
2. 对比端点路径、方法、参数、请求体和响应 schema。
3. 更新 service 类型和函数。
4. 更新 hooks/pages，使其消费带类型的 service。
5. 仅在需要时添加兼容处理，并说明原因。
