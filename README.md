# Échecs

讓角色坐在對面陪你下西洋棋，他會看盤、會教，也會記得你反覆犯的錯。

功能包含四檔難度對弈、求救提示、賽後講評、跨局記憶，以及角色卡與記憶包的匯出匯入。

## 開玩三步

1. 用 GitHub Pages 或本機 HTTP 伺服器開啟本頁，不要直接用 `file://`。
2. 右上打開設定，貼上 API 端點、金鑰、模型，並填好角色名。
3. 需要的話上傳角色卡或頭像，存好後直接開局。

本機測試可在資料夾內執行：

```bash
python -m http.server 8000
```

然後開 `http://127.0.0.1:8000/`。

## 金鑰教學

站內圖文版（拿金鑰六步、免費層確認、設定頁逐欄）在棋室大廳：`https://muxihana.github.io/chambre/guide.html`。

Google AI Studio 用法：

1. 到 Google AI Studio 建立 API key。
2. 端點填 `https://generativelanguage.googleapis.com/v1beta/openai`。
3. 模型建議先用 `gemini-3.1-flash-lite`。

如果你用 OpenRouter，端點可填 `https://openrouter.ai/api/v1`，再挑自己要的模型。

你的金鑰只存在你自己的瀏覽器 localStorage；只有在角色要開口或你按「撈清單」時，瀏覽器才會直接向你自己填的 API 端點送出請求，站方沒有後端、不經手任何資料。請只使用你信任的 API 供應商，別把金鑰貼進公開貼文、截圖或 issue；共用電腦用完記得按設定裡的「清除所有資料」。

## 隱私

這個頁面是純前端。角色設定、對話、記憶、戰績與金鑰都只存在你自己的瀏覽器 localStorage。

## 已知限制

- `file://` 直開會因 `chess.js` 的 ES module 載入限制失敗，請改用 Pages 或本機 HTTP 伺服器。
- 直接打 Anthropic 原生 API 不在這頁的預設相容路線內，建議改走 OpenRouter。
- 換瀏覽器或換裝置時，記憶不會自動跟著走，要自己匯出再匯入記憶包。
- 引擎第一次載入會抓約 7 MB 的 wasm，首局前可能要等一下。

## 授權

整個 repo 以 GNU General Public License v3.0 授權，全文見 [LICENSE](LICENSE)。

引擎使用 Stockfish.js 18，授權為 GPLv3；原始碼可參考 `github.com/nmrugg/stockfish.js` 與 `github.com/official-stockfish/Stockfish`。本頁自製程式同樣以 GPLv3 釋出。`vendor/chess.js` 來自 chess.js，授權為 BSD-2。
