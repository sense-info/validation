# 專案概述

## 專案名稱

Rakit Validation

## 專案定位

Rakit Validation 是一個獨立的 PHP 驗證函式庫，目標是提供易用、擴充性高、可自訂規則的資料驗證能力，適用於表單處理、API 請求驗證、以及資料集合法性檢查。

## 核心價值

- 以 Laravel 類似的驗證語法為設計靈感
- 讓 PHP 專案能在不依賴完整框架的情況下使用驗證能力
- 讓使用者能將自定義規則與錯誤訊息接入系統
- 支援巢狀資料與陣列元素驗證

## 專案範圍

本專案主要涵蓋：

- 基本欄位驗證（required、email、numeric、min、max 等）
- 條件式驗證（required_if、required_with 等）
- 陣列 / wildcard 驗證（例如 skills.*.id）
- 自訂 validation rule
- alias 與 message 設定
- uploaded file 驗證

## 非目標

- 不是完整的表單建構器
- 不是前端框架
- 不是資料庫 ORM
- 不是完整的 API Gateway

## 主要貢獻者角色

- 使用者：需要驗證資料合法性的 PHP 應用程式開發者
- 維護者：負責 framework 功能擴充與 bug 修正
- 貢獻者：新增規則、修正文件、補足測試

## 相關入口

- 專案首頁：README.md
- 核心實作：src/Validator.php
- 驗證規則：src/Rules
- 一般測試：tests/

## 對外影響

此庫的主要價值在於為 PHP 專案提供一致且可讀的資料驗證抽象，降低自建驗證邏輯的重複勞動，並讓開發者能快速宣告規則與錯誤訊息。
