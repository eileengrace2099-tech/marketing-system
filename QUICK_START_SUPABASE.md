# 🚀 Supabase 快速開始指南

## 📋 完成以下 3 個步驟，就能讓資料自動儲存到雲端！

---

## 步驟 1：建立 Supabase 專案（約 5 分鐘）

1. 前往 https://supabase.com
2. 使用 GitHub 帳號登入
3. 點擊「New Project」
4. 填寫：
   - Project Name: `marketing-system`
   - Database Password: 記下這個密碼（例如：`Marketing2024!System`）
   - Region: 選擇「Southeast Asia (Singapore)」
   - Plan: 選擇「Free」
5. 點擊「Create new project」
6. 等待 1-2 分鐘建立完成

---

## 步驟 2：取得 API 金鑰（約 2 分鐘）

1. 在 Supabase 專案中，點擊左側「Settings」
2. 點擊「API」
3. 複製以下兩個資訊：
   - **Project URL**（例如：`https://xxxxxxxxxxxxx.supabase.co`）
   - **anon public key**（很長的一串文字）

---

## 步驟 3：更新程式碼（約 1 分鐘）

1. 開啟 `index.html` 檔案
2. 找到第 34-35 行：
   ```javascript
   const SUPABASE_URL = ''; 
   const SUPABASE_KEY = '';
   ```
3. 將剛才複製的 URL 和 Key 貼上去：
   ```javascript
   const SUPABASE_URL = 'https://xxxxxxxxxxxxx.supabase.co';
   const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...';
   ```
4. 儲存檔案

---

## 步驟 4：建立資料庫表格（約 3 分鐘）

1. 在 Supabase 中，點擊左側「SQL Editor」
2. 點擊「New query」
3. 開啟 `SUPABASE_SETUP.md` 檔案
4. 複製「資料庫結構」區塊中的所有 SQL 指令
5. 貼到 SQL Editor 中
6. 點擊「Run」按鈕（或按 `Ctrl + Enter`）
7. 應該會看到「Success」訊息

---

## ✅ 完成！

現在開啟你的網站，應該會看到：
- 右上角顯示「☁️ 雲端同步」（表示已連線 Supabase）
- 所有資料會自動儲存到雲端
- 多台電腦可以同步資料

---

## 🆘 如果看到「💾 離線模式」

這表示 Supabase 還沒設定好，系統會自動使用 localStorage。

**檢查清單：**
- [ ] 是否已填入 SUPABASE_URL？
- [ ] 是否已填入 SUPABASE_KEY？
- [ ] 是否已建立資料庫表格？
- [ ] 按 `F12` 開啟 Console，查看是否有錯誤訊息

---

## 📖 詳細說明

如果需要更詳細的步驟說明，請查看 `SUPABASE_SETUP.md`

---

準備好了嗎？讓我們開始吧！🚀


