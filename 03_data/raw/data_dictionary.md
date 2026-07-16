# pre-ESRD 虛擬資料集 — 欄位說明 (Data Dictionary)

- **筆數**: 200 筆，每筆一位病人
- **族群**: pre-ESRD（多為 CKD 3b–5，baseline eGFR 集中在 15–45）
- **預測目標**: `renal_composite_endpoint`
- **注意**: 完全為教學用合成資料，非真實病人；已刻意加入少量遺漏值供資料清理練習

| 欄位 | 中文 | 型別 | 說明 |
|---|---|---|---|
| patient_id | 病人代碼 | 文字 | PE0001…PE0200 |
| age | 年齡 | 整數 | 歲 |
| sex | 性別 | 類別 | M / F |
| bmi | 身體質量指數 | 數值 | kg/m² |
| diabetes | 糖尿病 | 0/1 | |
| hypertension | 高血壓 | 0/1 | |
| cvd | 心血管疾病 | 0/1 | |
| gout | 痛風 | 0/1 | |
| sbp | 收縮壓 | 整數 | mmHg |
| dbp | 舒張壓 | 整數 | mmHg |
| baseline_egfr | 基線 eGFR | 數值 | mL/min/1.73m² |
| upcr_mg_g | 尿蛋白/肌酸酐比 | 整數 | mg/g（右偏分布）|
| hemoglobin | 血色素 | 數值 | g/dL |
| albumin | 白蛋白 | 數值 | g/dL |
| phosphate | 血磷 | 數值 | mg/dL |
| calcium | 血鈣 | 數值 | mg/dL |
| potassium | 血鉀 | 數值 | mEq/L |
| bicarbonate | 碳酸氫根 | 整數 | mEq/L |
| uric_acid | 尿酸 | 數值 | mg/dL |
| ldl | 低密度膽固醇 | 整數 | mg/dL |
| hba1c | 糖化血色素 | 數值 | % |
| raasi | ACEi/ARB 使用 | 0/1 | |
| sglt2i | SGLT2 抑制劑使用 | 0/1 | |
| diuretic | 利尿劑使用 | 0/1 | |
| statin | 他汀類使用 | 0/1 | |
| **renal_composite_endpoint** | **腎病組合終點** | **0/1** | **1 年內發生：進入透析(ESRD) / eGFR 下降 >40% / 腎因性死亡（任一）** |

## 內建的訊號（教學提示）
資料生成時，終點與下列因子有合理關聯，學生分析後應能看到：
- eGFR 越低 → 風險越高（事件組平均 21.4 vs 非事件組 29.8）
- 蛋白尿(UPCR)越高、糖尿病、心血管疾病、低白蛋白、貧血、高血磷 → 風險升高
- SGLT2i、RAASi 使用 → 具保護作用（風險降低）

事件發生率約 13%，屬於臨床上常見的不平衡類別（imbalanced），可順帶教 class imbalance 處理。

## 遺漏值
`bmi`、`upcr_mg_g`、`albumin`、`hba1c` 各有少量遺漏，適合練習資料清理與插補。
