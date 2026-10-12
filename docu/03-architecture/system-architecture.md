# 系統架構

## 架構概論

此專案的核心架構依賴三個主要層次：

1. `Validator`：對外入口，提供建立驗證任務的 API
2. `Validation`：處理驗證流程、欄位解析、規則檢查與錯誤收集
3. `Rule` / `Rules/*`：具體規則實作，負責單一驗證判斷

## 核心類別

### Validator

`src/Validator.php` 是主要對外介面，主要職責：

- 註冊和管理 rule
- 建立 `Validation` 實例
- 允許自訂 rule、訊息與翻譯設定
- 提供 `make()` 與 `validate()` API

### Validation

`src/Validation.php` 主要處理：

- 傳入資料解析
- attribute 與 rule 的關聯
- wildcard 欄位模式擴展
- 執行驗證流程
- 收集錯誤並存放到 `ErrorBag`

### Attribute

`src/Attribute.php` 用於代表每個欄位，包含：

- 欄位鍵值（例如 `email`、`skills.*.id`）
- 欄位別名
- 欄位規則集合
- 欄位的完整驗證狀態

### ErrorBag

`src/ErrorBag.php` 用於統一處理驗證錯誤，為上層開發者提供：

- 第一個錯誤
- 全部錯誤
- 依欄位分組的錯誤資料

## 規則設計

每個規則通常都繼承 `Rule`，該基類提供統一的介面，包括：

- `check()`：執行驗證
- `fillParameters()`：載入規則參數
- `setAttribute()`：設定目標欄位
- `isImplicit()`：判斷是否為隱含錯誤規則

實際規則位於 `src/Rules/`，例如：

- `Required`
- `Email`
- `Same`
- `UploadedFile`
- `Callback`
- `Between`

## 資料流

1. 使用者以 `Validator::make()` 或 `Validator::validate()` 建立驗證作業
2. 傳入原始輸入資料與規則陣列
3. `Validation` 將每個欄位轉為 attribute
4. 對每個 attribute 逐一套用 rule
5. 若規則失敗，收集到 `ErrorBag`
6. 最後返回驗證結果供程式判斷 `fails()` 或 `passes()`

## 設計重點

### 可擴充性
- 透過 `addValidator()` 可增加新的 rule
- 規則能在不修改核心控制流程的情況下擴充

### 可讀性
- 規則語法與 Laravel 類似
- 錯誤訊息能由 alias 與 message system 提升易讀性

### 模組化
- 核心驗證邏輯由 `Validator`、`Validation`、`ErrorBag` 與各 rule 分工
- 相對獨立，便於維護與測試

## 風險與限制

- 若輸入資料格式錯誤，可能需自行處理資料型別轉換
- 若自定義 rule 設計不佳，可能導致 rule name 衝突
- 多層巢狀資料驗證仍依賴正確的 key pattern

## 架構感知建議

後續擴充規則時，應遵循：

- 單一規則只負責單一責任
- 規則命名需清楚且符合驗證語意
- 若新規則有特殊參數，應保留在 `fillParameters()` 內處理
- 規則測試需涵蓋成功與失敗樣本
