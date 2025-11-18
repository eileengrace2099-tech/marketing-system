# 行銷管理系統

React + Tailwind 建置的行銷部專用管理系統，第一個完成的模組為「會員登入＋產品資料庫管理」。資料暫存於瀏覽器 `localStorage`，並提供匯出成 Word / Excel / PDF 的功能，方便作為廣告腳本、文案與銷售分析的基礎資料來源。

## 功能特色

- ✅ 會員登入／權限檢核（預設管理員帳密：`admin` / `admin`）
- ✅ 會員帳號管理：新增／編輯／刪除帳號、角色與模組授權
- ✅ 產品查找／分類篩選／全文搜尋
- ✅ 產品編號、品名、五大特色、通路貨號、圖片上傳（1:1）
- ✅ 通路管理：可維護通路清單並為每個產品輸入短網址
- ✅ 動態欄位：大分類、使用程序、受眾、痛點、得獎榮譽等皆可增刪修
- ✅ 多筆欄位：常見問答、推薦搭配產品、推薦其他產品、高轉換素材
- ✅ 匯出中心：勾選欄位後可輸出 Excel、Word、PDF，並提供匯出預覽
- ✅ LocalStorage 永續化＋JSON 結構，方便未來升級至雲端資料庫

## 快速開始

```bash
# 以 VS Code / 任意靜態伺服器啟動
cd marketing-system
npx serve .
```

或直接雙擊 `index.html`，即可於瀏覽器執行。

## 部署教學

1. **GitHub**
   1. 建立 repository（例：`marketing-system`）
   2. 將本專案檔案推送到 `main` 分支
2. **Zeabur**
   1. 登入 https://zeabur.com 並授權 GitHub
   2. 新增專案 → Add Service → Git → 選擇 `marketing-system`
   3. 類型選擇 **Static**，Build 設定可維持預設（本專案為純靜態）
   4. Deploy 後取得網址，例如 `https://marketing-system-xxxx.zeabur.app`

每次 `git push` 後 Zeabur 會自動重新部署。

## 目錄結構

```
marketing-system/
├── index.html   # React + Tailwind 單頁應用
├── README.md    # 本說明文件
└── .gitignore   # Git 忽略設定
```

## 常見問答

| 問題 | 解答 |
| --- | --- |
| 為什麼資料會消失？ | 目前資料儲存在瀏覽器 localStorage，若清除瀏覽紀錄會一起被清掉。請定期使用匯出功能備份。 |
| 想用多台電腦共享資料？ | 建議升級到雲端資料庫（如 Supabase / Firebase）；可再開新需求。 |
| 圖片容量太大怎麼辦？ | 建議壓縮或改成外部 CDN 連結。若日後接後端，可將圖片儲存在物件儲存服務。 |

## 後續 Roadmap

- 建立廣告文案管理模組
- 廣告成效／銷售儀表板
- LINE 官方帳號自動化腳本串接
- 後端 API 與雲端資料庫（PostgreSQL / Supabase）

有需要擴充或協助部署，歡迎提出需求！ 🚀

