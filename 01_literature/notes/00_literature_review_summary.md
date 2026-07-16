# 文獻回顧總覽 — pre-ESRD 腎病進展預測

> 版本：v0.1（2026-07-16）｜對應研究計畫 `02_planning/research_proposal.md`
> 目的：整理與本研究（1 年腎病組合終點預測）相關的既有證據，確立預測因子選擇、方法學與定位（gap）。

## 1. 主題地圖

| 主題 | 重點文獻 | 對本研究的意義 |
|---|---|---|
| A. 風險預測方程（KFRE） | Tangri 2011 (JAMA); Tangri 2016 (JAMA, 多國驗證) | 建立 baseline 可比較的臨床標準；4/8 變項組合是特徵選擇的依據 |
| B. 機器學習預測 | Cureus 2024 系統性回顧; Lei 2022 meta-analysis; Sci Rep 2022 | ML AUROC 約 0.84–0.89，與 KFRE 相當或略優；支持本研究比較 LR vs ML |
| C. 關鍵預測因子（蛋白尿/eGFR/白蛋白） | Iseki 2013 (Nat Rev Nephrol); eGFR+UACR 合用 | 佐證假說：低 eGFR、高 UPCR、低白蛋白 → 風險↑ |
| D. 治療的保護作用（SGLT2i/RAASi） | Heerspink 2020 (DAPA-CKD); EMPA-KIDNEY 2023 | 佐證假說：SGLT2i/RAASi 具腎臟保護；亦影響變項解讀與臨床定位 |

## 2. 各主題摘要

### A. 腎衰竭風險方程（KFRE）
- **Tangri 2011（JAMA）**：以加拿大 CKD 3–5 期兩世代開發並驗證預測模型，預測 2/5 年進展至腎衰竭。含 age、sex、eGFR、UACR 的 4 變項模型表現良好；加入 calcium、phosphate、bicarbonate、albumin 的 8 變項模型更準確。→ 現稱 KFRE，已被 KDIGO 指引採納。
- **多國驗證（Tangri 2016）**：於 30+ 世代、逾 70 萬名 CKD G3–G5 病人驗證，跨洲別 discrimination 佳（C 統計量約 0.90）。
- **本研究連結**：我們的資料含 KFRE 8 變項中的多數（eGFR、albumin、phosphate、calcium、bicarbonate），UPCR 可近似 UACR。可將「KFRE 類」變項組合作為 baseline 特徵集。

### B. 機器學習預測 CKD 進展
- **系統性回顧（Cureus 2024）**：涵蓋 LR、SVM、隨機森林、神經網路等，ESRD 預測 AUROC 約 0.84–0.89；預測全死因死亡率（all-cause mortality）的 AUROC 較低（約 0.75–0.77）。
- **Meta-analysis（Lei 2022）**：LR、naïve Bayes、隨機森林三者預測力相當，且相較 KFRE 有更高的敏感度。
- **本研究連結**：支持以 logistic regression 為 baseline，再比較正則化/樹模型；並提醒重視 discrimination 與 calibration，而非僅 accuracy。

### C. 關鍵預測因子
- **蛋白尿（Iseki 2013, Nat Rev Nephrol）**：蛋白尿嚴重度越高，eGFR 下降越快，且與 baseline eGFR 無關；支持以蛋白尿辨識高風險者。
- **eGFR + UACR 組合**：兩者合用比單一指標更能預測進展；UACR 上升與 eGFR 下降各自對應數倍的 ESKD 風險。
- **本研究連結**：直接支持將 `baseline_egfr`、`upcr_mg_g`、`albumin` 納入模型；UPCR 右偏，建議 log 轉換（見 SAP）。

### D. 治療的保護作用
- **DAPA-CKD（Heerspink 2020, NEJM）**：4304 名 CKD（eGFR 25–75、UACR 200–5000），dapagliflozin 顯著降低「eGFR 下降≥50% / ESKD / 腎或心血管死亡」組合終點，含糖尿病與非糖尿病族群。
- **EMPA-KIDNEY（2023）**：納入 eGFR 低至 ≥20 的族群，empagliflozin 使腎病進展或心血管死亡的組合風險降低約 28%。
- **本研究連結**：佐證 `sglt2i`、`raasi` 使用作為保護性變項；同時提醒，用藥為治療決策的結果（可能有適應症混淆 confounding by indication），解讀係數時需謹慎。

## 3. 研究缺口（Gap）與本研究定位
1. 既有模型多預測 2–5 年腎衰竭；本研究聚焦**較短的 1 年組合終點**，適合教學情境展示不平衡類別處理。
2. 多數 ML 研究重 discrimination，較少完整報告 **calibration**；本研究將同時報告 AUROC/AUPRC 與校準。
3. 以小型（n=200）合成資料示範**可重現的完整流程**（清理→建模→評估→報告），作為 AI 課程範例。

## 4. 對後續分析的具體影響
- 特徵集：以 KFRE 類變項為核心，加入共病與用藥。
- 轉換：`upcr_mg_g` log 轉換；連續變項標準化。
- 評估：AUROC（主）、AUPRC、校準曲線 / Brier；k-fold CV，`random_state=42`。
- 詮釋：用藥變項小心 confounding by indication。

## 5. 待補
- [ ] 補充 diabetic kidney disease 專屬預測模型（Frontiers 2026 meta-analysis）之細節。
- [ ] 尋找亞洲/台灣族群 pre-ESRD 世代研究以增進外推性。
- [ ] 檢視是否有 1 年短期終點的既有模型可直接對照。

---
*完整引用見 `99_references/references.bib`；單篇細讀筆記見同目錄其他 `.md` 檔。*
