# 研究計畫書（Research Proposal）

> 狀態：草稿 v0.1 — 待補文獻與細節

## 1. 研究背景與動機
慢性腎臟病（CKD）進入末期腎病（ESRD）前的 pre-ESRD 階段，若能及早辨識高風險病人，有機會透過藥物（如 SGLT2i、RAASi）與監測延緩惡化。本研究以臨床常規檢驗資料，建立 1 年腎病組合終點的預測模型。

## 2. 研究問題（PICO）
- **P（族群）**：pre-ESRD 病人（多為 CKD 3b–5，baseline eGFR 約 15–45）。
- **I / 預測因子**：人口學、共病、生命徵象、腎功能與代謝相關檢驗、用藥。
- **C（比較）**：不同模型（logistic regression baseline vs. 機器學習模型）。
- **O（結果）**：1 年內 `renal_composite_endpoint`（進入透析 / eGFR 下降 >40% / 腎因性死亡，任一）。

## 3. 假說
1. 較低 baseline eGFR、較高 UPCR、糖尿病、心血管疾病、低白蛋白、貧血、高血磷 → 事件風險上升。
2. SGLT2i、RAASi 使用 → 事件風險下降（保護作用）。

## 4. 資料
- 來源：`03_data/raw/preesrd_dataset.csv`（200 筆，合成教學資料）。
- 資料字典：`03_data/raw/data_dictionary.md`。
- 結果變項事件率約 13%（不平衡類別）。
- 已知遺漏：`bmi`, `upcr_mg_g`, `albumin`, `hba1c`。

## 5. 統計分析計畫（摘要，詳見 SAP）
- 描述性統計：事件 vs. 非事件組比較（table 1）。
- 遺漏值處理：先描述缺失比例與機制，採用中位數／多重插補（待定，記錄理由）。
- 建模：logistic regression baseline → 正則化 / 樹模型；處理類別不平衡。
- 評估：AUROC、AUPRC、校準曲線、混淆矩陣；交叉驗證，固定 `random_state=42`。

## 6. 產出
- 分析程式（`04_code/`）、實驗紀錄（`06_experiments/`）、圖表（`05_analysis/`）、論文（`08_manuscript/`）。

## 7. 倫理
- 合成資料，無真實病人，無需 IRB；真實研究時此節需補倫理審查資訊。

## 8. 時程
見 `00_admin/project_plan.md`。
