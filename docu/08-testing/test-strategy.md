# 測試策略

## 測試目標

- 驗證所有核心 rule 行為
- 確認例外情境與錯誤訊息正常
- 確保巢狀資料與陣列驗證正確
- 保持自訂 rule 擴充能力穩定

## 測試範圍

### 單元測試

覆蓋：

- `required`
- `email`
- `numeric`
- `min` / `max` / `between`
- `same`
- `in` / `not_in`
- `array`
- `uploaded_file`

### 整合測試

覆蓋：

- `Validator::make()`
- `Validator::validate()`
- `errors()` 輸出
- custom messages
- aliases
- wildcard data

## 測試原則

1. 成功與失敗案例分開測試
2. 每個 rule 至少一個正向與一個反向案例
3. 異常條件必須測試 exception 行為
4. 大型整合案例需驗證 data flow

## 測試執行方式

```bash
./vendor/bin/phpunit
```

## 建議新增案例

- 自訂 rule 成功註冊
- 覆蓋內建 rule 時拋出 exception
- 巢狀資料 `foo.*.bar` 驗證
- `nullable` 行為
- `callback` 驗證

## 驗收標準

- 核心功能測試全數通過
- bug 修正需附加 regression test
- 新增 rule 必須同步更新文件與範例
