# 🔧 疑難排解指南

## 問題：網站顯示空白頁

### 解決方案 1：檢查 Zeabur 設定

1. **進入 Zeabur 專案**
   - 登入 https://zeabur.com
   - 進入你的 `marketing-system` 專案

2. **檢查服務設定**
   - 點擊你的服務
   - 進入 `Settings` 標籤
   - 確認以下設定：
     - **Framework Preset**: `Static` 或 `Other`
     - **Root Directory**: 留空（或設為 `.`）
     - **Build Command**: 留空
     - **Output Directory**: 留空（或設為 `.`）

3. **重新部署**
   - 在服務頁面點擊 `Redeploy`
   - 或進入 `Settings` → `General` → `Redeploy`

### 解決方案 2：檢查檔案是否正確上傳

1. **檢查 GitHub**
   - 前往你的 GitHub repository
   - 確認 `index.html` 在根目錄
   - 確認所有檔案都已 commit 並 push

2. **檢查 Zeabur Logs**
   - 在 Zeabur 服務頁面點擊 `Logs` 標籤
   - 查看是否有錯誤訊息
   - 確認檔案是否正確讀取

### 解決方案 3：手動設定輸出目錄

如果自動偵測失敗，手動設定：

1. 進入服務的 `Settings`
2. 找到 `Build & Deploy` 區塊
3. 設定：
   - **Output Directory**: `.`
   - **Root Directory**: `.`
4. 點擊 `Save` 並重新部署

### 解決方案 4：檢查瀏覽器 Console

1. 開啟網站
2. 按 `F12` 開啟開發者工具
3. 切換到 `Console` 標籤
4. 查看是否有錯誤訊息
5. 切換到 `Network` 標籤
6. 重新整理頁面，檢查 `index.html` 是否成功載入

### 解決方案 5：清除快取

1. **清除瀏覽器快取**
   - 按 `Ctrl + Shift + Delete`（Windows）或 `Cmd + Shift + Delete`（Mac）
   - 選擇清除快取
   - 重新整理頁面

2. **使用無痕模式測試**
   - 開啟無痕視窗
   - 訪問網站測試

## 問題：無法登入

### 解決方案

1. **確認帳號密碼**
   - 帳號：`admin`
   - 密碼：`admin`

2. **清除 localStorage**
   - 按 `F12` 開啟開發者工具
   - 切換到 `Console` 標籤
   - 輸入：`localStorage.clear()`
   - 重新整理頁面

3. **使用登入頁面的重置功能**
   - 在登入頁面點擊「若無法登入，點此清除本機資料並重設」
   - 確認清除後重新登入

## 問題：功能無法正常運作

### 解決方案

1. **檢查瀏覽器相容性**
   - 建議使用 Chrome、Firefox、Edge 最新版本
   - 避免使用過舊的瀏覽器

2. **檢查 JavaScript 是否啟用**
   - 確認瀏覽器已啟用 JavaScript
   - 檢查是否有擴充功能阻擋 JavaScript

3. **檢查 Console 錯誤**
   - 按 `F12` 開啟開發者工具
   - 查看 `Console` 是否有錯誤訊息
   - 將錯誤訊息截圖給我協助診斷

## 問題：資料遺失

### 解決方案

1. **資料儲存在 localStorage**
   - 資料只存在於當前瀏覽器
   - 清除瀏覽器資料會導致資料遺失
   - 建議定期使用「匯出」功能備份

2. **多台電腦無法共享**
   - 目前資料儲存在瀏覽器本地
   - 不同電腦的資料是分開的
   - 未來升級雲端版本後可解決此問題

## 需要進一步協助？

如果以上方法都無法解決問題，請提供：
1. 瀏覽器 Console 的錯誤訊息（截圖）
2. Zeabur Logs 的內容（截圖）
3. 問題發生的具體步驟

我會協助你進一步診斷問題！

