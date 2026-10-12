# ADR 0001: 採用類似 Laravel 的驗證 API

## 狀態

Accepted

## 背景

專案需要提供一套簡潔、熟悉且易於擴充的資料驗證接口。若直接設計成底層函數式 API，使用者需記住較多低層細節；若採用宣告式規則語法，開發者能更快上手並維持一致性。

## 決策

採用 `Validator::make($inputs, $rules)` / `Validator::validate($inputs, $rules)` 的 API 設計，並以字串規則語法描述驗證邏輯，例如：

```php
$validator->validate($data, [
    'email' => 'required|email',
    'password' => 'required|min:8'
]);
```

## 理由

- 符合 Laravel 使用者心智模型
- 可讀性高，寫法簡潔
- 便於擴充新的 rule
- 適合用於表單與 API 請求情境

## 反方意見

- 直接呼叫函數式驗證較少依賴 magic string
- 但這會降低開發者可讀性與一致性

## 影響

- 使用者需熟悉 rule 字串格式
- `Validation` 類別需要處理多階段解析
- 需要維持對 rule name 的一致命名規範

## 後續跟進

- 確保規則解析與例外有一致的錯誤時機
- 持續補充 file validation 與 custom rule 範例
