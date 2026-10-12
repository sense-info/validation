# Sprint 01 紀錄

## 目標

- 建立驗證函式庫基礎結構
- 確認核心 API 風格與使用方式
- 補齊基本測試與文件

## 完成項目

- 建立 `Validator` 入口
- 實作 `Validation` 驗證流程
- 建立 `ErrorBag` 錯誤輸出能力
- 提供基本 rules（required、email、numeric 等）
- 補充 README 文件與使用範例

## 遇到的問題

1. 多層陣列欄位驗證需要較精細的 key 解析機制
2. 驗證錯誤顯示需保持可讀但不失程式可用性
3. 自訂 rule 覆寫需要避免內建 rule 被誤改

## 決策

- 採用類似 Laravel 的宣告式驗證語法
- 將錯誤處理集中在 `ErrorBag`
- 以 `Validation` 為核心控制流程，讓 rule 保持模組化

## 下一步

- 加強 wildcard 資料驗證測試
- 補齊 ADR 與 release note 文件
- 擴充自訂 rule 範例與訊息模板

## 狀態

已完成基礎型別驗證功能與文件建立。
