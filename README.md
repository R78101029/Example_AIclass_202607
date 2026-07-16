# pre-ESRD 腎病組合終點預測研究專案

> AI 課程研究範例專案 — 以 Claude Code 協助完成從文獻、規劃、資料清理、統計分析、實驗到論文撰寫的完整研究流程。

## 專案概述

- **研究主題**：以 pre-ESRD（慢性腎臟病 3b–5 期）病人的臨床與檢驗資料，預測 1 年內腎病組合終點（進入透析 / eGFR 下降 >40% / 腎因性死亡）。
- **資料**：200 筆合成教學資料（`03_data/raw/preesrd_dataset.csv`），事件發生率約 13%（不平衡類別）。
- **預測目標**：`renal_composite_endpoint`（0/1）。
- **狀態**：規劃中（見 `02_planning/research_proposal.md`）。

> ⚠️ 本資料為**教學用合成資料**，非真實病人資料，不得用於任何臨床決策。

## 資料夾結構

| 資料夾 | 用途 |
|---|---|
| `00_admin/` | 專案管理：時程、待辦、IRB/倫理相關文件 |
| `01_literature/` | 文獻蒐集（`papers/` PDF）與閱讀筆記（`notes/`） |
| `02_planning/` | 研究計畫書、假說、分析計畫（SAP） |
| `03_data/` | 資料：`raw/`（原始，唯讀）、`interim/`（中間）、`processed/`（分析用）、`external/`（外部參考） |
| `04_code/` | 程式碼：`src/`（可重用模組）、`notebooks/`（探索式分析） |
| `05_analysis/` | 分析產出：`statistics/`、`figures/`、`tables/` |
| `06_experiments/` | 建模實驗，每個實驗一個子資料夾（含設定與結果） |
| `07_results/` | 彙整後的最終結果 |
| `08_manuscript/` | 論文：`drafts/`、`figures/`、`submission/` |
| `09_logs/` | 研究紀錄：`research_log/`（研究日誌）、`meeting_notes/`（會議） |
| `99_references/` | 引用書目（BibTeX 等） |

## 研究流程（建議順序）

1. **文獻回顧** → `01_literature/`
2. **規劃與假說** → `02_planning/`
3. **資料清理與 EDA** → `03_data/` + `04_code/notebooks/`
4. **統計分析與建模** → `04_code/src/` + `05_analysis/` + `06_experiments/`
5. **結果彙整** → `07_results/`
6. **論文撰寫** → `08_manuscript/`
7. **全程紀錄** → `09_logs/research_log/`（每次進度都留下 log）

## 環境設定

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 與 Claude Code 協作

專案協作守則寫在 `CLAUDE.md`，Claude 會依該檔的原則管理資料夾、記錄研究日誌、維持可重現性。

## 資料來源與授權

- 資料字典：`03_data/raw/data_dictionary.md`
- 合成資料，僅供教學；請勿散布為真實臨床資料。
