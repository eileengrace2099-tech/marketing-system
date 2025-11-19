# 🚀 Supabase 雲端資料庫設定指南（小白版）

本指南會一步一步教你如何設定 Supabase，讓你的行銷管理系統資料自動儲存到雲端。

---

## 📋 第一步：註冊 Supabase 帳號

### 步驟 1：前往 Supabase 官網

1. 開啟瀏覽器
2. 前往：https://supabase.com
3. 點擊右上角的 **「Start your project」** 或 **「Sign in」**

### 步驟 2：使用 GitHub 帳號註冊（推薦）

1. 點擊 **「Continue with GitHub」**
2. 授權 Supabase 存取你的 GitHub
3. 完成註冊

**為什麼用 GitHub？**
- 最簡單快速
- 不需要另外記密碼
- 安全性高

---

## 📋 第二步：建立新專案

### 步驟 1：建立專案

1. 登入後，點擊 **「New Project」** 按鈕
2. 填寫專案資訊：

   **Organization（組織）**
   - 如果是第一次使用，會自動建立一個組織
   - 直接使用預設的即可

   **Project Name（專案名稱）**
   - 輸入：`marketing-system`
   - 或任何你喜歡的名稱

   **Database Password（資料庫密碼）**
   - ⚠️ **重要**：這個密碼要記下來！
   - 建議：使用一個強密碼（至少 12 個字元）
   - 例如：`Marketing2024!System`
   - 💡 **小技巧**：可以寫在記事本，但不要分享給別人

   **Region（地區）**
   - 選擇：**「Southeast Asia (Singapore)」** 或 **「Northeast Asia (Tokyo)」**
   - 這會影響速度，選離台灣最近的

   **Pricing Plan（方案）**
   - 選擇：**「Free」**（免費方案）
   - 免費方案對小團隊完全夠用

3. 點擊 **「Create new project」**
4. ⏳ 等待 1-2 分鐘，讓 Supabase 建立專案

---

## 📋 第三步：取得 API 金鑰

### 步驟 1：進入專案設定

1. 專案建立完成後，點擊左側選單的 **「Settings」**（設定）
2. 點擊 **「API」**

### 步驟 2：複製需要的資訊

你會看到以下資訊，**全部複製下來**（我會告訴你放在哪裡）：

1. **Project URL**
   - 長得像：`https://xxxxxxxxxxxxx.supabase.co`
   - 複製這個網址

2. **anon public key**
   - 長得像：`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`
   - 這是一串很長的文字
   - 複製這個金鑰

3. **service_role key**（選填，進階使用）
   - 先不用管這個

### 步驟 3：儲存這些資訊

💡 **建議**：建立一個文字檔，暫時儲存：
```
Project URL: https://xxxxxxxxxxxxx.supabase.co
API Key: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

---

## 📋 第四步：建立資料庫表格

### 步驟 1：進入 SQL Editor

1. 在 Supabase 左側選單，點擊 **「SQL Editor」**
2. 點擊 **「New query」**

### 步驟 2：貼上 SQL 指令

我會提供 SQL 指令給你，你只需要：

1. **複製我提供的 SQL 指令**（在下面的「資料庫結構」區塊）
2. **貼到 SQL Editor 中**
3. 點擊 **「Run」** 按鈕（或按 `Ctrl + Enter`）
4. 應該會看到「Success. No rows returned」的訊息

### 步驟 3：確認表格已建立

1. 點擊左側選單的 **「Table Editor」**
2. 應該會看到以下表格：
   - `users`（會員資料）
   - `products`（產品資料）
   - `reference_options`（參考選項）

---

## 📋 第五步：設定 API 權限（安全性）

### 步驟 1：進入 Authentication 設定

1. 點擊左側選單的 **「Authentication」**
2. 點擊 **「Policies」**

### 步驟 2：設定表格權限

我會提供詳細的權限設定步驟，但基本原則是：
- 只有登入的使用者可以讀取自己的資料
- 管理員可以讀寫所有資料
- 公開資料（如產品列表）可以讓所有人讀取

---

## 📋 第六步：更新程式碼

### 步驟 1：在程式碼中加入 Supabase 設定

我會修改你的 `index.html`，加入 Supabase 的設定。

你需要做的：
1. 找到程式碼中的這一段：
   ```javascript
   const SUPABASE_URL = '你的 Project URL';
   const SUPABASE_KEY = '你的 API Key';
   ```
2. 將剛才複製的 URL 和 Key 貼上去

### 步驟 2：測試連線

1. 開啟網站
2. 按 `F12` 開啟開發者工具
3. 切換到 `Console` 標籤
4. 應該會看到「Supabase 連線成功」的訊息

---

## 📋 資料庫結構

以下是需要建立的表格 SQL 指令：

```sql
-- 1. 建立 users 表格（會員資料）
CREATE TABLE IF NOT EXISTS users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  username TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL,
  email TEXT,
  display_name TEXT,
  role TEXT DEFAULT 'member',
  permissions JSONB DEFAULT '{"products": false, "ads": false}',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- 2. 建立 products 表格（產品資料）
CREATE TABLE IF NOT EXISTS products (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  product_number TEXT,
  category TEXT,
  usage_flow TEXT,
  usage_method TEXT,
  name_zh TEXT,
  name_en TEXT,
  nickname TEXT,
  short_description TEXT,
  purchase_decision TEXT,
  channel_links JSONB DEFAULT '{}',
  features JSONB DEFAULT '[]',
  audiences JSONB DEFAULT '[]',
  pain_points JSONB DEFAULT '[]',
  awards JSONB DEFAULT '[]',
  images JSONB DEFAULT '[]',
  channel_skus JSONB DEFAULT '[]',
  recommended_combos JSONB DEFAULT '[]',
  recommended_others JSONB DEFAULT '[]',
  high_conversion_assets JSONB DEFAULT '[]',
  faqs JSONB DEFAULT '[]',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- 3. 建立 reference_options 表格（參考選項）
CREATE TABLE IF NOT EXISTS reference_options (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  option_key TEXT UNIQUE NOT NULL,
  options JSONB DEFAULT '[]',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- 4. 插入預設管理員帳號
INSERT INTO users (username, password, email, display_name, role, permissions)
VALUES (
  'admin',
  'admin',
  'admin@example.com',
  '系統管理員',
  'admin',
  '{"products": true, "ads": false}'
)
ON CONFLICT (username) DO NOTHING;

-- 5. 插入預設參考選項
INSERT INTO reference_options (option_key, options)
VALUES 
  ('categories', '["保養", "美妝", "生活家電"]'),
  ('usageFlows', '["日常保養", "彩妝步驟", "深層清潔"]'),
  ('usageMethods', '["早晚使用", "睡前使用", "運動前後"]'),
  ('audiences', '["女性", "男性", "青少年", "敏感肌"]'),
  ('painPoints', '["出油", "暗沉", "痘痘", "乾裂"]'),
  ('awards', '["FG 特優", "女人我最大推薦", "百大網友口碑"]'),
  ('channelLinks', '["官網", "蝦皮", "屈臣氏"]')
ON CONFLICT (option_key) DO NOTHING;
```

---

## 📋 常見問題

### Q: 忘記資料庫密碼怎麼辦？

A: 
1. 進入專案設定 → Database
2. 可以重設密碼，但需要重新設定連線

### Q: API Key 洩露了怎麼辦？

A: 
1. 進入 Settings → API
2. 可以重新產生新的 Key
3. 記得更新程式碼中的 Key

### Q: 免費額度用完了怎麼辦？

A: 
1. 可以升級到付費方案（$25/月）
2. 或優化資料使用量
3. 或考慮自建後端

### Q: 如何備份資料？

A: 
1. 進入 Database → Backups
2. 可以手動建立備份
3. 或設定自動備份

---

## 📋 下一步

完成以上步驟後，告訴我：
1. ✅ 已建立 Supabase 專案
2. ✅ 已取得 API URL 和 Key
3. ✅ 已建立資料庫表格
4. ✅ 已更新程式碼中的設定

我會協助你測試並確認一切正常運作！

---

## 🆘 需要協助？

如果遇到任何問題：
1. 截圖錯誤訊息給我
2. 告訴我卡在哪個步驟
3. 我會協助你解決

準備好了嗎？讓我們開始吧！🚀


