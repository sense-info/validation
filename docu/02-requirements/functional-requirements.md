# 功能需求

## 1. 基本驗證能力

### 1.1 required
- 需要確保欄位存在且不為空。
- 適用於表單資料與請求資料。

### 1.2 email / url / numeric / integer
- 驗證常見資料型別與格式。
- 讓開發者能在單一規則中完成格式檢查。

### 1.3 min / max / between / digits / digits_between
- 驗證長度、數值範圍與位數。

## 2. 條件式驗證

### 2.1 required_if / required_unless / required_with
- 當特定條件成立時，要求欄位存在。
- 可處理多欄位依賴場景。

## 3. 陣列與巢狀資料

### 3.1 wildcard 支援
- 支援 `skills.*.id`、`tags.*` 等資料結構驗證。
- 可對陣列元素逐一檢查。

### 3.2 嵌套路徑解析
- 能將點記號欄位名稱轉為陣列結構，便於驗證。

## 4. 自訂訊息與別名

### 4.1 setAlias / setAliases
- 允許欄位以容易閱讀的名稱呈現錯誤訊息。

### 4.2 setMessages
- 允許定義全域或單次驗證的錯誤訊息。

## 5. 自訂規則

### 5.1 addValidator
- 使用者可註冊自定義驗證規則。
- 規則可重用於不同驗證場景。

### 5.2 callback rule
- 提供一種方法將自訂函式直接接入驗證流程。

## 6. 檔案驗證

### 6.1 uploaded_file
- 驗證檔案是否存在且符合限制。

### 6.2 mimes / extension
- 檢查檔案型別與副檔名。

## 7. 驗證結果輸出

- `fails()` 可判斷是否驗證失敗
- `errors()` 可取得 `ErrorBag`
- 支援逐筆錯誤、第一個錯誤、全部錯誤的取得方式

## 8. 例外與錯誤處理

- 若規則不存在，應拋出明確 exception
- 若 rule 覆蓋行為不安全，應保護內建規則不被覆寫

## 需求優先順序

1. 基本 rule 與資料型別驗證
2. 條件式驗證與 nested data support
3. 自訂訊息、別名與 rule 擴充
4. 檔案驗證能力
5. 文件與範例完善
