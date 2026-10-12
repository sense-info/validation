# 開發環境設定

## 需求

- PHP 7.0 或以上
- Composer
- 可用的 PHP CLI 環境
- 建議安裝 PHPUnit 以執行測試

## 安裝步驟

```bash
composer install
```

如果要直接使用此套件：

```bash
composer require "rakit/validation"
```

## 專案啟動

此專案本身主要是函式庫，不需要啟動伺服器。常見使用模式為：

```php
<?php

require 'vendor/autoload.php';

use Rakit\Validation\Validator;

$validator = new Validator();
$validation = $validator->make($_POST, [
    'email' => 'required|email',
    'password' => 'required|min:8',
]);

$validation->validate();

if ($validation->fails()) {
    print_r($validation->errors()->firstOfAll());
}
```

## 測試執行

```bash
./vendor/bin/phpunit
```

或在專案根目錄執行：

```bash
vendor/bin/phpunit
```

## 開發建議

- 新增驗證規則時，先補測試再實作
- 優先維持與 Laravel 驗證 API 一致的使用者體驗
- 每個規則應遵守單一責任原則
- 需保留向後相容的行為，除非有明確版本變更

## Git 工作流建議

- 功能開發使用分支
- 提交前先執行測試
- 重要變更應同步更新文檔與 release notes
- 重大設計變更需附帶 ADR
