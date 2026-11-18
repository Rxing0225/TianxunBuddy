# 天寻 Buddy V4.3.0 开发审查版

Vue 3 / TypeScript 前端与 FastAPI 后端。基于已脱敏的 V4.2.6 技术审查源码合入 V4.3.0 PRD V2 更新，保留合成/测试数据及旧版源码脱敏。

本次新增投标工作台、工序驾驶舱、返工闭环、双轨提取合成、广联达任务书与回读校验等接口，并升级项目、工程量、定额、计价页面的结构化表单。

`production_accepted=false`；`accuracy_E=BLOCKED`。这是开发审查版本，已知权限与业务门禁问题见 [升级审查](docs/UPGRADE_REVIEW.md)。

前端：在 `frontend` 执行 `npm ci --ignore-scripts`、`npm run dev` 或 `npm run build`。后端依赖见 `backend/requirements.txt`，测试在 `backend/tests`；运行前配置独立测试环境与身份数据。不要使用真实业务数据验证开发代码。

验证摘要：145 个 Python 文件静态编译通过，前端构建通过（63 modules）；87 项既有回归与 12 项 smoke 断言通过。上述结果来自隔离验证副本，未完成全量回归、部署、业务准确性或生产验收。

前端包版本已设为 4.3.0；后端历史包元数据和健康接口仍保留旧版标识，详见升级审查。来源与逐文件哈希见 `SOURCE_MANIFEST.json`。

本仓库未附加开源 LICENSE，许可和真实数据授权说明见 [DATA_LICENSE_STATUS.md](DATA_LICENSE_STATUS.md)。第三方依赖沿用各自许可；保留源码已有版权及必要署名。
