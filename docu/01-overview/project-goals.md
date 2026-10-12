# 專案目標

## 目標

1. 提供簡潔且一致的驗證 API。
2. 支援大多數常見的資料驗證需求。
3. 讓資料驗證能在 PHP 專案中獨立使用，而不受框架限制。
4. 支援自訂規則、欄位別名與錯誤訊息語系化。
5. 維持程式碼的可擴充性與模組化。

## 成功條件

- 能使用 `Validator::make()` 或 `Validator::validate()` 進行資料檢查
- 可驗證單一欄位與巢狀資料陣列
- 可透過自訂 rule 擴充驗證能力
- 可輸出可讀的錯誤訊息格式
- 測試覆蓋主要驗證場景

## 非目標

- 完整表單處理流程
- DB 操作與資料持久化
- 若需更完整的業務邏輯，應由上層應用自行處理

## 優先級

### P1（核心）
- 基本 rule
- array / nested attribute handling
- custom messages
- validation result object

### P2（重要）
- uploaded file validation
- alias support
- rule override strategy
- localization-ready message pattern

### P3（延伸）
- 高階驗證能力與更多自訂規則
- 文件改善與範例擴充

## 長期願景

使此專案成為一個可以在多種 PHP 應用中重複使用的驗證基礎元件，並在社群中保持穩定、簡潔且可擴充的規則設計。
