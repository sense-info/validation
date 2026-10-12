# Sprint 02：升級至 PHP 8.5

## 目標

將專案升級並驗證可在 PHP 8.5 環境中建置、測試與執行，同時維持既有的功能行為與相容性。

## Sprint 範圍

- 確認目前專案在 PHP 8.5 下的相容性狀態
- 升級 Composer / development dependency 版本
- 修正 PHP 8.5 可能出現的 deprecation、behavior change 與 runtime issue
- 更新 CI / local test 環境
- 驗證 package 仍可正確安裝與使用
- 補充文件與發布說明

## 工作計畫

### Phase 1：基線評估與風險盤點

#### 任務 1.1：建立 PHP 8.5 基線
- 目的：確認目前程式碼與工具鏈在 PHP 8.5 下的實際狀態
- 內容：
  - 檢查 `composer.json` 的 PHP 版本限制
  - 檢查 PHPUnit / coding standard 版本是否支援 PHP 8.5
  - 以 PHP 8.5 CLI 執行基線測試
- 輸出：
  - 相容性清單
  - 需要修正的兼容性項目
  - 依賴升級清單

#### 任務 1.2：收斂已知 incompatibility
- 目的：找出目前可能被 PHP 8.5 拋棄或改變的行為
- 內容：
  - 檢查 `src/` 內使用了可能受 PHP 8.5 影響的 API
  - 檢查 `tests/` 是否有假設依賴舊版 PHP 行為
  - 檢查 `composer` 依賴是否有新版本需求
- 輸出：
  - incompatibility checklist
  - risk register

### Phase 2：依賴與工具鏈升級

#### 任務 2.1：更新 Composer 版本需求
- 內容：
  - 檢查 `php` constraint 從 `>=7.0` 是否要調整為 `>=8.5` 或保留較低版本支援
  - 評估是否需要維持向下相容
- 決策點：
  - 是否維持最低 PHP 版本（如 `>=7.4`）
  - 或直接升級到 PHP 8.5 最低版本門檻

#### 任務 2.2：更新 dev dependencies
- 內容：
  - 升級 PHPUnit 至支援 PHP 8.5 的版本
  - 檢查 php_codesniffer 是否仍支援 PHP 8.5
  - 檢查 coveralls / CI plugin 是否仍可運作
- 輸出：
  - 更新後的 `composer.json`
  - lockfile 更新結果

### Phase 3：程式碼相容性修正

#### 任務 3.1：修正 PHP 8.5 兼容性問題
- 內容：
  - 修正 deprecated function / API usage
  - 檢查可用的 `#[
  - 修正 dynamic property / property visibility / type compatibility 問題
  - 處理 array access / string offset 行為改動
- 重點：
  - 保持 library 的 public behavior 一致
  - 不因升級而破壞既有 API

#### 任務 3.2：更新測試案例
- 內容：
  - 補足 PHP 8.5 環境下的 regression tests
  - 修正 outdated assertions
  - 補強 edge cases
- 輸出：
  - updated tests
  - validation result coverage

### Phase 4：CI / 品質驗證

#### 任務 4.1：更新 CI matrix
- 內容：
  - 在 GitHub Actions / CI 中加入 PHP 8.5
  - 若有多版本測試，補上 PHP 7.x / 8.x 兼容策略
- 輸出：
  - CI config 更新
  - 測試結果報告

#### 任務 4.2：執行品質檢查
- 內容：
  - `composer test`
  - phpunit
  - phpcs
  - 啟動 package-level smoke test
- 輸出：
  - 綜合測試結果
  - 可接受的風險清單

### Phase 5：文件與交付

#### 任務 5.1：更新文件與發布說明
- 內容：
  - 更新 README 版本需求
  - 補充 PHP 8.5 兼容說明
  - 新增 upgrade note / migration note
- 輸出：
  - release notes
  - compatibility docs

#### 任務 5.2：整理 release summary
- 內容：
  - 說明此次升級範圍
  - 列出已修正的 breaking changes
  - 說明後續支援策略

## 預估時程

- Phase 1：1 天
- Phase 2：1 天
- Phase 3：2–3 天
- Phase 4：1 天
- Phase 5：0.5–1 天

總計：約 5–7 天

## 風險與注意事項

- 依賴套件可能不支援 PHP 8.5，需先確認替代版本
- 升級 PHP 版本可能帶來 deprecation 或 subtle behavior changes
- 若同時維持舊版 PHP 相容，可能增加兼容性負擔
- `composer.json` 必須清楚定義明確的支援範圍

## 驗收標準

- 專案可在 PHP 8.5 環境中成功安裝與執行
- `phpunit` 全數通過
- `phpcs` 通過
- README / documentation 更新完成
- 版本與 release notes 明確記錄此次變更

## 進度狀態

- [ ] Phase 1：基線評估
- [ ] Phase 2：依賴升級
- [ ] Phase 3：程式碼修正
- [ ] Phase 4：CI / 品質驗證
- [ ] Phase 5：文件與交付

## 備註

此 sprint 的主要目的是確保升級到 PHP 8.5 時，不只是單純修改 `composer.json`，而是要完整確認所有支援層、測試層、文件層與發布層都能同步正常運作。
