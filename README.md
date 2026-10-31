# 你的第一場 FRC 區域賽（情境模擬）

給 FRC 新隊員用的網頁模擬：走完一場區域賽（Pit、檢錄、場地量測、排位賽、聯盟選擇、淘汰賽），每個選擇都對照 2026 賽季比賽手冊（TU22）的規則給回饋。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 遊戲本體（畫面、計分與規則判定）。 |
| `questions.json` | 所有題目文字：標題、情境說明、選項、結果、規則說明。 |

只有這兩個檔案，沒有任何建置步驟。

## 放上 GitHub Pages

1. 建立一個 GitHub repository，把 `index.html`、`questions.json`、`README.md` 放在根目錄並 commit。
2. 到 repository 的 **Settings → Pages**。
3. **Source** 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 Save。
4. 等一兩分鐘，網址會是 `https://你的帳號.github.io/repository名稱/`。

## 修改題目

方法一：直接改 `questions.json`，commit 後重新整理網頁就會生效。

方法二：在網頁上改。
1. 右上角按「編輯題目」，逐題修改文字。
2. 按「下載題目檔」，得到新的 `questions.json`。
3. 用它取代專案裡的 `questions.json`，commit。

編輯畫面也能「載入題目檔」，用來預覽別人傳來的題目。

在網頁上改的內容會暫存在該瀏覽器，首頁會顯示「清除本機修改」。要讓所有人看到，一定要更新專案裡的 `questions.json`。

### 題目檔的規則

- 只改文字，不要改 `id`，也不要增減或調換 `c`（選項）的順序。
- 情境說明裡這些標記會在遊玩時自動換成實際內容，可以移動或刪除，但請保留大括號：
  `{rank}` 排名、`{rp}` 目前 RP、`{rs}` Ranking Score、`{record}` 戰績、`{capnote}`、`{picknote}`、`{bracket}`、`{result}`。
- 文字中的 `<`、`>`、`&` 會被自動換成全形。

## 不在題目檔裡的東西

這些寫在 `index.html`：計分模型、機率、違規判定、每個選項對機器能力的影響。要改這些，需要修改程式。

## 本機預覽

直接開啟 `index.html` 也能玩，但瀏覽器會擋住讀取 `questions.json`，所以會使用內建的預設文字。要預覽修改後的題目，請在專案資料夾執行：

```
python3 -m http.server
```

然後開啟 `http://localhost:8000`。

## 限制

- 場上得分、故障與對手強度是簡化模型，只有規則依據與結果的因果對照手冊。
- 淘汰賽只模擬幾場關鍵比賽（完整是 6 輪）。
- 沒有評審獎項，也沒有 FIRST Championship 的 4 隊聯盟版本。
- 規則以 2026 比賽手冊 TU22 為準，之後的 Team Update 若有變動，需要自行核對題目文字。
