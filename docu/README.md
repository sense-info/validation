# Documentation Center

這個目錄用於保存專案說明文件與開發歷程，讓專案知識能長期保留、可追溯與可維護。

## 目錄結構

- 01-overview/
  - project-overview.md: 專案介紹、範圍與背景
  - project-goals.md: 目標、成功條件與非目標
- 02-requirements/
  - functional-requirements.md: 功能需求列表
  - change-log.md: 需求/變更歷程紀錄
- 03-architecture/
  - system-architecture.md: 系統架構與核心模組
- 04-design/
  - feature-design.md: 功能設計與實作方向
- 05-development/
  - setup-guide.md: 開發環境與啟動方式
- 06-implementation-history/
  - sprint-log/sprint-01.md: 版本/迭代歷程
- 07-decisions/
  - adr/0001-validation-core-design.md: 關鍵設計決策紀錄
- 08-testing/
  - test-strategy.md: 測試策略與驗收方式
- 09-operations/
  - operations-guide.md: 維運與發布指引
- 10-release/
  - release-notes/v1.0.0.md: 發布紀錄
- 12-retrospectives/
  - retrospective-template.md: 回顧模板
- 13-templates/
  - template-task.md: 任務記錄模板

## 專案定位

本專案是 Rakit Validation PHP library，核心目標是提供一個 standalone 的資料驗證框架，支援：

- 常見欄位驗證規則
- 多層陣列/巢狀資料驗證
- 自訂驗證規則與錯誤訊息
- 上傳檔案驗證
- 可讀的錯誤結果與別名處理

## 文件使用建議

- 新成員可先閱讀 01-overview 與 05-development
- 想了解功能與規則請看 02-requirements
- 想看系統設計與架構可看 03-architecture
- 想了解開發變更與歷程請看 06-implementation-history 與 07-decisions
- 想準備發布或回歸測試請看 08-testing 與 10-release

## 維護規則

1. 每個功能新增或重大調整，需同步更新需求與設計文件。
2. 每個重要決策需要補充 ADR。
3. bug 修正需記錄問題描述、根因、修正內容與驗證方式。
4. 每次版本發佈後須更新 release notes。
5. 文件內容需保留背景、原因與決策脈絡，不能只保存結果。

## 更新紀錄

- 2026-10-12: 建立 docu 目錄與基礎文件結構
