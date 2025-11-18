# 🚀 部署指南 - GitHub + Zeabur

本指南將協助你將行銷管理系統部署到 GitHub 並透過 Zeabur 上線。

---

## 📋 前置準備

1. **GitHub 帳號**：如果還沒有，請前往 https://github.com 註冊
2. **Zeabur 帳號**：如果還沒有，請前往 https://zeabur.com 註冊（可使用 GitHub 帳號登入）

---

## 步驟 1：上傳到 GitHub

### 方法 A：使用 GitHub Desktop（推薦新手）

1. **下載 GitHub Desktop**
   - 前往：https://desktop.github.com/
   - 下載並安裝
   - 用你的 GitHub 帳號登入

2. **建立新 Repository**
   - 點擊 `File` → `New Repository`
   - 填寫資訊：
     - **Name**: `marketing-system`
     - **Description**: `行銷管理系統 - 產品資料庫與廣告文案管理`
     - **Local Path**: 選擇 `\\Eg-nas\行銷企劃部\sophia\marketing-system`
     - ✅ 勾選「Initialize this repository with a README」（如果還沒有的話）
   - 點擊 `Create Repository`

3. **Commit 並 Push**
   - 回到 GitHub Desktop
   - 左下角填寫：
     - **Summary**: `初始版本 - 完整功能部署`
     - **Description**: `包含登入系統、產品管理、會員管理、匯出功能`
   - 點擊 `Commit to main`
   - 點擊 `Publish repository`
   - ✅ 確認「Keep this code private」（如果不想公開）
   - 點擊 `Publish Repository`

✅ **完成！** 你的程式碼已經上傳到 GitHub 了！

### 方法 B：使用命令列（進階使用者）

```bash
# 1. 切換到專案目錄
cd "\\Eg-nas\行銷企劃部\sophia\marketing-system"

# 2. 初始化 git（如果還沒初始化）
git init

# 3. 加入所有檔案
git add .

# 4. 提交
git commit -m "初始版本 - 完整功能部署"

# 5. 連接到 GitHub（先在 GitHub 網頁建立 repository）
git remote add origin https://github.com/你的帳號/marketing-system.git

# 6. 推送
git branch -M main
git push -u origin main
```

---

## 步驟 2：部署到 Zeabur

### 2.1 註冊並登入 Zeabur

1. 前往：https://zeabur.com
2. 點擊右上角 `Sign In`
3. 選擇 `Continue with GitHub`
4. 授權 Zeabur 存取你的 GitHub

### 2.2 建立專案

1. 登入後，點擊 `Create Project`
2. 輸入專案名稱：`marketing-system`
3. 選擇地區：`Hong Kong`（離台灣最近，速度最快）
4. 點擊 `Create`

### 2.3 部署服務

1. 在專案頁面，點擊 `Add Service`
2. 選擇 `Git`
3. 選擇你的 GitHub Repository：`marketing-system`
4. Zeabur 會自動偵測這是靜態網站
5. 點擊 `Deploy`

⏳ **等待 1-2 分鐘...**

### 2.4 設定網域

1. 部署完成後，點擊你的服務
2. 切換到 `Domains` 標籤
3. Zeabur 會自動生成一個網址，例如：
   - `marketing-system-xxx.zeabur.app`
4. 點擊網址即可開啟你的系統！

### 2.5（選用）綁定自訂網域

如果你有自己的網域：

1. 在 `Domains` 標籤點擊 `Add Domain`
2. 輸入你的網域，例如：`marketing.yourcompany.com`
3. 按照指示到你的 DNS 服務商（如 Cloudflare）設定 CNAME
4. 等待 DNS 生效（通常 5-10 分鐘）

---

## ✅ 測試與驗證

### 1. 開啟網站

前往你的 Zeabur 網址

### 2. 測試登入

- 帳號：`admin`
- 密碼：`admin`

### 3. 測試功能

- ✅ Dashboard 顯示正常
- ✅ 點擊「產品資料庫」進入模組
- ✅ 新增一個測試產品
- ✅ 上傳圖片（會自動裁切成 1:1）
- ✅ 測試匯出功能
- ✅ 進入「會員管理系統」新增帳號

### 4. 測試資料持久性

- 重新整理頁面
- 登出再登入
- 資料應該還在（儲存在瀏覽器 localStorage）

---

## 🔄 未來更新流程

當你修改程式碼後：

### 使用 GitHub Desktop

1. 開啟 GitHub Desktop
2. 會自動顯示你的修改
3. 填寫 Commit 訊息
4. 點擊 `Commit to main`
5. 點擊 `Push origin`
6. ⚡ Zeabur 會自動重新部署（約 1-2 分鐘）

### 使用命令列

```bash
git add .
git commit -m "新增廣告文案管理功能"
git push
```

Zeabur 會自動檢測 GitHub 更新並重新部署！

---

## 💰 Zeabur 費用說明

### 免費額度

- 每月 $5 USD 免費額度
- 包含流量和運算資源
- 小團隊完全夠用

### 計費方式

- 靜態網站幾乎不耗費資源
- 預計每月 $0-2 USD
- 只有在超過免費額度才計費

### 監控用量

1. 到 Zeabur Dashboard
2. 點擊右上角帳號圖示
3. 選擇 `Billing`
4. 查看當月用量

---

## 🆘 常見問題

### Q: 網站打不開？

**A:**
1. 檢查 Zeabur 部署狀態是否為「Running」
2. 確認網域設定正確
3. 清除瀏覽器快取

### Q: 資料會遺失嗎？

**A:**
- 目前資料儲存在瀏覽器 localStorage
- 清除瀏覽器資料會導致遺失
- 建議定期使用「匯出」功能備份
- 未來升級雲端版本後資料會永久保存

### Q: 如何讓團隊成員使用？

**A:**
1. 分享 Zeabur 網址給團隊
2. 由管理員建立使用者帳號
3. 設定對應權限
4. 團隊成員用自己的帳號密碼登入

### Q: 手機可以用嗎？

**A:**
- 可以！介面是響應式設計
- 手機、平板都能正常使用
- 建議用電腦操作以獲得最佳體驗

### Q: 怎麼升級到雲端資料庫？

**A:**
- 需要建立後端 API
- 使用 PostgreSQL 資料庫
- 我可以協助你升級（需要修改程式碼）
- 預估成本：$5-10 USD/月

---

## 📞 需要協助？

如果遇到任何問題：

1. **檢查 Zeabur Logs**
   - 在 Zeabur 服務頁面點擊 `Logs`
   - 查看是否有錯誤訊息

2. **檢查 GitHub**
   - 確認程式碼已成功推送
   - 查看最新的 commit

3. **聯絡我**
   - 把錯誤訊息截圖給我
   - 我會協助你解決

---

## 🎉 恭喜！

你的行銷管理系統已經成功部署上線了！

**系統網址**: `https://你的網址.zeabur.app`

**管理員帳號**:
- 帳號：`admin`
- 密碼：`admin`

⚠️ **重要提醒**:
- 請盡快修改管理員密碼
- 定期備份資料（使用匯出功能）
- 監控 Zeabur 用量

準備好了嗎？讓我們開始建立更多功能模組吧！🚀

