# Tangri 2011 — 腎衰竭風險方程（KFRE）原始論文

- **引用**：Tangri N, Stevens LA, Griffith J, et al. A predictive model for progression of chronic kidney disease to kidney failure. *JAMA*. 2011;305(15):1553–1559.
- **BibTeX key**：`tangri2011kfre`
- **主題分類**：A. 風險預測方程
- **連結**：https://pubmed.ncbi.nlm.nih.gov/21482743/

## 研究問題
能否用常規臨床/檢驗資料，準確預測 CKD 3–5 期病人進展至腎衰竭？

## 方法
- 兩個獨立加拿大世代（開發 + 驗證），CKD 3–5 期（eGFR 10–59），轉介腎臟科病人。
- 結果：進展至腎衰竭（透析或移植）。
- 比較不同變項數的模型（含 4 變項與 8 變項）。

## 主要結果
- **4 變項**（age, sex, eGFR, albuminuria）已有良好表現。
- **8 變項**（再加 calcium、phosphate、bicarbonate、albumin）更準確。
- 模型在驗證世代 discrimination 佳（C 統計量高）。

## 對本研究的意義
- 提供 baseline 特徵集的依據；我們的資料含 eGFR、albumin、phosphate、calcium、bicarbonate，`upcr_mg_g` 可近似 albuminuria。
- 可建立「KFRE 類」變項組合，與我們的 logistic baseline 對照。

## 侷限 / 注意
- 原始終點為 2–5 年腎衰竭，與本研究 1 年組合終點不同，不能直接套用係數。
- 轉介腎臟科族群，外推至一般照護需驗證。

## 關鍵詞
KFRE, CKD progression, prediction model, eGFR, albuminuria
