# 機器學習預測 CKD 進展 — 回顧與統合分析

- **主題分類**：B. 機器學習預測
- **BibTeX keys**：`khalid2024mlckd`, `lei2022mlmeta`, `bai2022mlesrd`

## 涵蓋文獻
1. **系統性回顧（Cureus 2024）** — Predicting the Progression of CKD: A Systematic Review of AI/ML Approaches.
   連結：https://pmc.ncbi.nlm.nih.gov/articles/PMC11166249/
2. **Meta-analysis（Lei 等 2022）** — ML algorithms' accuracy in predicting kidney disease progression.
   連結：https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9341041/
3. **Bai 等 2022（Sci Rep）** — Machine learning to predict ESRD in CKD.
   連結：https://www.nature.com/articles/s41598-022-12316-z

## 重點整理
- 常用演算法：logistic regression、SVM、隨機森林、神經網路 / 深度學習。
- **表現**：ESRD 預測 AUROC 約 **0.84–0.89**；預測全死因死亡率（all-cause mortality）的 AUROC 較低（約 0.75–0.77）。
- LR、naïve Bayes、隨機森林三者預測力相當，且相較 KFRE 有更高**敏感度**。
- 結論：ML 可作為 ESRD 與死亡風險分層的輔助工具，支持個人化管理。

## 對本研究的意義
- 支持研究設計：以 **logistic regression 為 baseline**，再比較正則化 / 樹模型（隨機森林、梯度提升）。
- 提醒評估重點應含 **discrimination（AUROC/AUPRC）與 calibration**，而非僅 accuracy——尤其在事件率約 13% 的不平衡情境。
- 小樣本（n=200）下，複雜模型易過擬合；需交叉驗證與正則化，並誠實報告不確定性。

## 侷限 / 注意
- 多數研究樣本量與族群差異大，AUROC 直接跨研究比較須謹慎。
- 報告品質不一，calibration 常被忽略。

## 關鍵詞
machine learning, CKD progression, ESRD, AUROC, calibration, class imbalance
