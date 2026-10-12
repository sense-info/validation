# 維運與發布指引

## 目標

確保開發、測試、發布與例行維護流程具備一致性，讓專案可以穩定持續演進。

## 日常維運

- 檢查依賴與 PHP 版本相容性
- 確認測試案例執行正常
- 追蹤 issue 與 bug 修正狀態
- 更新 release notes 和 docs

## 發布前檢查

1. 執行完整測試
2. 檢查範例程式是否正常
3. 確認文件與版本資訊同步
4. 確認 release note 包含更新內容

## 發布流程

```bash
composer test
# 或
./vendor/bin/phpunit
```

然後更新版本資訊、tag 與 release notes。

## 問題處理

- 若新增功能造成回歸，需補寫 regression test
- 若變更影響 API 使用方式，需在 release note 中說明
- 如果存在破壞性變更，需在文件中強調 migration note

## 維運指標

- 測試通過率
- 例外回歸數量
- issue 回覆與修正時間
- 文件同步程度
