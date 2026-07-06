# 稟文書寫

道場稟文生成工具，已封裝為可離線使用的 PWA（Progressive Web App）。

## 線上使用

部署到 Vercel 後，網址格式為：

```
https://<你的專案名稱>.vercel.app/
```

手機瀏覽器開啟後，可選「加入主畫面」，即可像 App 一樣使用（含離線快取）。

## 檔案結構

```
index.html        主程式（表單、農曆換算、輸出、LINE 分享）
manifest.json     PWA 設定檔（名稱、圖示、顯示模式）
sw.js             Service Worker（離線快取）
vercel.json       Vercel 部署設定
icons/            App 圖示（192x192、512x512）
```

## 將 GitHub 改為 Private

1. 開啟 https://github.com/chelseaweng/bingwen-app/settings
2. 捲到最下方 **Danger Zone**
3. 點 **Change repository visibility**
4. 選擇 **Make private**，依提示輸入 repo 名稱確認

> Private repo 仍可透過 Vercel 部署，需在 Vercel 連結 GitHub 並授權存取該 repo。

## 部署到 Vercel（Private Repo）

### 第一次設定

1. 前往 https://vercel.com 並用 GitHub 帳號登入
2. 點 **Add New… → Project**
3. 選擇 **Import Git Repository**，找到 `bingwen-app`
   - 若看不到 private repo：到 Vercel **Settings → Git** → **Adjust GitHub App Permissions** → 授權存取 private repos
4. 專案設定：
   - **Framework Preset**：Other
   - **Root Directory**：`./`（預設即可）
   - **Build Command**：留空
   - **Output Directory**：留空（或 `.`）
5. 點 **Deploy**，等待完成
6. 部署成功後會得到網址，例如 `https://bingwen-app.vercel.app`

### 之後更新

推送至 `main` 分支後，Vercel 會自動重新部署。

## 停用 GitHub Pages（建議）

改由 Vercel 部署後，可到 GitHub repo **Settings → Pages**，將 Source 改為 **None**，避免重複部署。

## 注意事項

- 若日後更新 `index.html` 內容，記得同步更新 `sw.js` 內的 `CACHE_NAME`（例如改成 `bingwen-v7`），否則使用者裝置上的舊快取可能不會立即更新。
- 本工具的農曆換算資料表涵蓋西元 1900–2100 年（即民國 -11 至 189 年），超出範圍將無法換算。
