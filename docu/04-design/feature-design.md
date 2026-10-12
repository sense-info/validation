# 功能設計

## 設計目標

為了維持驗證 API 的一致性，gathering a validation rule system and error outputs should be clear, reusable, and environment-independent.

## 主要設計決策

### 1. 設計成 standalone library
- 不綁定 Laravel 或其他框架
- 讓 PHP 專案可以直接依賴

### 2. 核心輸入是 `inputs + rules`
- 使用者提供原始資料與規則宣告
- 驗證邏輯在 `Validation` 類別中集中解析

### 3. 規則以獨立對象存在
- 每個規則只負責一項判斷
- 便於擴充與測試

### 4. 錯誤資料統一收斂在 ErrorBag
- 提供可讀性與程式判斷的雙重能力

## 範例流程

```php
$validator = new \Rakit\Validation\Validator;
$validation = $validator->make($_POST, [
    'email' => 'required|email',
    'password' => 'required|min:8'
]);

$validation->validate();

if ($validation->fails()) {
    $errors = $validation->errors();
}
```

## 影響面

- 對使用者而言：API 簡潔、熟悉
- 對維護者而言：規則可維護、測試可管理
- 對獲得擴充而言：可增加 custom rule 與 message

## 風險

- 規則長度過長時可讀性下降
- 若規則名稱不一致，容易造成難以維護的使用體驗

## 後續優化

- 補充更高階的組合規則設計
- 擴大 alias / localization 協作能力
