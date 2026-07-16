# 統計分析計畫（Statistical Analysis Plan, SAP）

> 在進行任何分析前先固定本計畫，避免事後挑選（p-hacking）。修改需在 `09_logs/research_log/` 記錄理由。

## 1. 分析資料集
- 主分析：完整病例 / 插補後資料（見第 4 節）。
- 單位：每筆一位病人（n=200）。

## 2. 主要與次要結果
- 主要結果：`renal_composite_endpoint`（0/1）。
- 事件率預期約 13%（不平衡）。

## 3. 描述性統計（Table 1）
- 連續變項：平均±標準差或中位數(IQR)，依分布選擇。
- 類別變項：n(%)。
- 事件組 vs. 非事件組比較（t-test / Mann-Whitney / chi-square，依適用性）。

## 4. 遺漏值處理
- 先報告各變項缺失比例（`bmi`, `upcr_mg_g`, `albumin`, `hba1c`）。
- 策略（擇一並記錄）：完整病例分析、中位數插補、或多重插補（MICE）。
- 敏感度分析：比較不同插補策略的結果穩健性。

## 5. 變項處理
- `upcr_mg_g` 右偏 → 考慮 log 轉換。
- 連續變項標準化（建模需要時）。
- 避免資料洩漏：所有轉換／插補參數只在訓練集擬合。

## 6. 建模
- Baseline：logistic regression。
- 進階：正則化 logistic（L1/L2）、隨機森林 / 梯度提升。
- 類別不平衡：class weight、或重抽樣（SMOTE），記錄選擇。

## 7. 驗證與評估
- k-fold 交叉驗證（k=5），固定 `random_state=42`。
- 指標：AUROC（主）、AUPRC、校準曲線 / Brier score、敏感度/特異度。
- 報告 95% 信賴區間。

## 8. 顯著水準
- 雙尾 α = 0.05；多重比較時說明校正方式。

## 9. 軟體
- Python（見 `requirements.txt`）；固定亂數種子確保可重現。
