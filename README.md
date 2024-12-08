# Wazuh API Postman 使用說明

## 檔案說明

本專案包含兩個主要檔案：
- `Wazuh API.postman_collection.json`：Postman API 集合檔案
- `wazuh-environment.json`：環境變數設定檔案

## 功能特點

### 自動令牌更新機制
集合中包含自動化的令牌（Token）管理機制，具有以下特點：
- 在發送請求前自動檢查令牌是否存在
- 自動驗證現有令牌是否有效
- 當令牌不存在或已過期時，自動取得新令牌
- 使用環境變數中的認證資訊進行令牌更新

### API 端點分類
集合中的 API 端點依功能分類：
- 基本資訊
- 代理程式管理
- 群組管理
- 叢集管理
- MITRE
- 規則管理
- 安全性設定
- 系統檢查
- 任務管理

## 環境設定

### 必要的環境變數
在 `wazuh-environment.json` 中需要設定以下變數：
- `baseUrl`：Wazuh API 的基礎 URL
- `username`：API 認證用戶名
- `password`：API 認證密碼
- `token`：用於儲存認證令牌（會自動更新）

### 設定步驟
1. 在 Postman 中匯入 `Wazuh API.postman_collection.json` 檔案
2. 匯入 `wazuh-environment.json` 環境設定檔
3. 確認環境變數中的 `baseUrl`、`username` 和 `password` 已正確設定

## 使用方式

1. 在 Postman 中選擇已匯入的環境
2. 執行任何 API 請求時，系統會：
   - 自動檢查令牌狀態
   - 必要時自動更新令牌
   - 使用有效的令牌發送請求

## 注意事項

- 所有 API 請求都使用 Bearer Token 認證
- 令牌更新是自動進行的，無需手動處理
- 環境變數中的敏感資訊（如密碼和令牌）應妥善保管
- 建議定期更新認證資訊以確保安全性

## 疑難排解

如果遇到認證問題：
1. 確認環境變數中的認證資訊正確
2. 檢查 `baseUrl` 是否可以訪問
3. 確認使用者帳號具有適當的存取權限
