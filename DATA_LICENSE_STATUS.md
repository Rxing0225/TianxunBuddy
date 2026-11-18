# DATA_LICENSE_STATUS

## 1. 结论先行

| 项 | 状态 |
|---|---|
| 开源许可（LICENSE） | **未附加** — 权利人未确认，不得视为可自由再分发 |
| 真实业务数据外部交付 | **BLOCKED_BY_DATA_PERMISSION** |
| 仓库可见性 | **Private**（数据授权未闭环前不得公开） |

## 2. 数据授权登记（TD-001 / TD-002 / TD-003）

| data_id | 名称 | 权利人 | 授权状态 | 内部测试 | 外部交付 | 再分发 | 本次发布处置 |
|---|---|---|---|---|---|---|---|
| TD-001 | 土建清单 | 待业务方确认 | UNVERIFIED | 是 | **否** | **否** | 排除，不入库；以合成夹具替代 |
| TD-002 | 安装清单 | 待业务方确认 | UNVERIFIED | 是 | **否** | **否** | 排除，不入库；以合成夹具替代 |
| TD-003 | 郑州Q3价格PDF | 待业务方确认 | PARTIAL | 是 | **否** | **否** | 排除，不入库；以合成夹具替代 |

## 3. 具体被排除的内容

共 21 个文件因含 TD-001/002/003 内容被移出发布包，包括：

- 清单行数据（`BOQ_50.json`、`BOQ_98.json`、`BOQ_VALIDATION.*`）；
- 材料价格数值与勘误（`MATERIAL_PRICE_VALIDATION.*`）；
- 原始导出工作簿（`TEST_ONLY_SAMPLE.xlsx`、`TEST_ONLY_API_SAMPLE.xlsx`
  ——**文件名标注 TEST_ONLY，内容却是真实清单**，属本次发现的问题之一）；
- 语料盘点与原始文件哈希（`*_DATA_INVENTORY.json`、`OCR_CONTENT_DEDUP.json`、
  `OCR_HUMAN_REVIEW_READINESS.*`）；
- 含真实请求体的 API 记录（`API_REQUESTS.json`、`API_RESULTS.json`）；
- 引用真实数值的叙述文档（`V4.2.6_真实业务验证报告.md`）。

逐文件清单、大小、SHA256 与理由见各包 `INTEGRITY/EXCLUDED_FILES.csv`。
**原始文件未被删除**，仍在本地受控环境中。

## 4. 替代方案：合成测试数据

发布包内提供自主生成的合成夹具（`03_TEST_DATA/fixtures`）：

| 文件 | 行数 | 与真实资料的区别 |
|---|---|---|
| `SYNTHETIC_土建清单_20行.xlsx` | 20 | 编码前缀 `SYN-`，项目名虚构，工程量构造 |
| `SYNTHETIC_安装清单_15行.xlsx` | 15 | 同上 |
| `SYNTHETIC_材料价格_24行.csv` | 24 | 地域为 `SYN-REGION-A/B`，价格为构造值 |

**严禁**把合成数据的结果描述为真实业务结论；用合成数据跑通只证明机制可用。

## 5. 仍存在的元数据暴露（需授权评审确认）

| 位置 | 内容 | 判定 |
|---|---|---|
| `backend/txbuddy/pilot/importer.py` | 地域标识「郑州市」、期次记录条数常量（5026 / 5024 / 939 / 10989）、一个勘误 CSV 文件名 | **LOW**：仅元数据，无单价、无行内容 |
| `backend/txbuddy/governance/catalog.py` | 原真实项目名 | 已替换为 `REAL_PROJECT_Sxx` 别名 |

## 6. 解除阻断的条件

1. 权利人出具 TD-001/002/003 的书面外部交付与再分发授权；
2. 明确授权范围（对象、用途、期限、地域）；
3. 更新 `DATA_PERMISSION_REGISTER.csv` 并把 `external_delivery` 改为 YES；
4. 重新打包并挂接到 Release —— **不得**在未授权前把验收包对外分发。

## 7. 许可

本项目许可状态不明确，仓库未附开源 LICENSE。
在权利人书面确认前，代码、文档与数据的复制、修改、再分发权利均未授予。
