# 稟文書寫

道場稟文生成工具，已封裝為可離線使用的 PWA（Progressive Web App）。

## 線上使用

部署到 GitHub Pages 後，網址格式為：

```
https://<你的GitHub帳號>.github.io/<repo名稱>/
```

手機瀏覽器開啟後，可選「加入主畫面」，即可像 App 一樣使用（含離線快取）。

## 檔案結構

```
index.html        主程式（表單、農曆換算、輸出、LINE 分享）
manifest.json      PWA 設定檔（名稱、圖示、顯示模式）
sw.js              Service Worker（離線快取）
icons/             App 圖示（192x192、512x512）
```

## 部署到 GitHub Pages 步驟

1. 在 GitHub 建立一個新的 repository（例如 `bingwen-app`），設為 Public。
2. 把這個資料夾內所有檔案（保持資料夾結構）上傳到該 repo 的根目錄（或上傳到 `main` 分支）。
3. 進入 repo 的 **Settings → Pages**。
4. 在 **Build and deployment** 區塊：
   - Source 選擇 **Deploy from a branch**
   - Branch 選擇 **main**，資料夾選擇 **/(root)**
   - 按 **Save**
5. 等待約 1 分鐘，畫面會顯示網址，例如：
   `https://你的帳號.github.io/bingwen-app/`
6. 開啟該網址即可使用；手機上可加入主畫面安裝為 App。

## 注意事項

- 若日後更新 `index.html` 內容，記得同步更新 `sw.js` 內的 `CACHE_NAME`（例如改成 `bingwen-v2`），否則使用者裝置上的舊快取可能不會立即更新。
- 本工具的農曆換算資料表涵蓋西元 1900–2100 年（即民國 -11 至 189 年），超出範圍將無法換算。
