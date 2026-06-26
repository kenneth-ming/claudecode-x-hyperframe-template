# 肆季動畫模板 — 快速上手

歡迎!這是一個 HyperFrames 動畫模板。跟著步驟做,你只要**貼上你的台詞(SRT),就能生成跟範例同一個風格的動畫影片**。
完整教學請看老師另外給的《從 0 到 1》教學文件,這裡是精簡版。

---

## 一、第一次使用要先做(只做一次)

### 1. 安裝基礎環境
- 安裝 Node.js(22 版以上):https://nodejs.org
- 安裝 FFmpeg:
  - Windows:PowerShell 打 `winget install Gyan.FFmpeg`
  - Mac:終端機打 `brew install ffmpeg`
- 確認:`node -v`(要 v22 以上)、`ffmpeg -version`(有跑出資訊就 OK)

### 2. 啟動 Claude Code(二選一)
- **桌面版**:下載 Claude 桌面版 → 登入 → 切到「Code」分頁
- **VS Code**:擴充套件搜「Claude Code」(裝 Anthropic 官方的)→ 點橘色星星 → 登入
- ※ 需要付費的 Claude 帳號

### 3. 安裝 HyperFrames(讓 Claude Code 學會做動畫)
在 Claude Code 貼這句:
> 請讀 https://github.com/heygen-com/hyperframes ,把 HyperFrames 的 skills
> 安裝給 Claude Code 使用。我是 Windows/Mac 環境。裝好告訴我可以開始了。

---

## 二、做你的動畫(每次都這樣,三步)

### STEP 1 — 換成你的影片
把你的口播影片放進 `assets` 資料夾,**檔名命名為 `my-footage.mp4`**(直接覆蓋範例的那支)。
> 📏 建議影片長度跟範例差不多(避免動畫時間點對不上)。比較長也沒關係,跟 Claude Code 講你的影片秒數即可。

### STEP 2 — 貼上你的台詞,讓 Claude Code 生成
準備好你的字幕檔(SRT 格式,有時間碼 + 台詞)。在 Claude Code 貼這句:

```
請先讀 ANIMATION_GUIDE.md,然後根據我下面的 SRT 台詞,在這個專案生成對應的動畫。
我的影片已放在 assets/my-footage.mp4,比例要【9:16 給 IG / 16:9 給 YT】。
請先跟我說你的動畫規劃,我確認後再寫。

【在這裡貼上你的 SRT】
```

Claude Code 會讀「動畫規則(ANIMATION_GUIDE.md)」+ 你的台詞,**照範例的風格**幫你生成動畫。
它會先說它的規劃,你點頭後它才開始寫。

### STEP 3 — 預覽 → 輸出
```
npx hyperframes preview
```
打開它給的網址(像 http://localhost:3002)看效果。不滿意就回 Claude Code 講要改什麼。

滿意後輸出影片:
```
npx hyperframes render
```
會產生一支 mp4 影片檔。完成!🎬
（⚠️ 不要用預覽畫面的 Export 按鈕,它常失敗;用上面的指令。）

---

## 三、想微調?直接用講的

動畫出來後,想調整就繼續跟 Claude Code 說,例如:
- 「第 3 句的 icon 換成購物車」
- 「結尾的金色光暈再強一點」
- 「文字放大、往上移一點,不要擋到我的臉」
- 「節奏太趕,把每個動作的間隔拉開」

---

## 四、卡住了?

| 狀況 | 解法 |
|---|---|
| Export 按鈕失敗 | 別用按鈕,終端機打 `npx hyperframes render` |
| 預覽說找不到瀏覽器 | 先打 `npx hyperframes browser ensure` 再 preview |
| 中文變方框 | 跟 Claude Code 說「中文用 Noto Sans TC」 |
| 說超過輸出上限 | 跟它說「分批寫入 index.html,不要一次輸出整份」 |
| 動畫變成一頁頁切換、不連貫 | 跟它說「照 ANIMATION_GUIDE 的規則,用 icon 連貫說故事」 |

---

## 資料夾說明

- `index.html` — 動畫主檔(Claude Code 會改這個,你通常不用手動動)
- `ANIMATION_GUIDE.md` — **動畫風格規則**(讓你貼 SRT 就能生成同風格動畫的關鍵)
- `compositions/` — 動畫場景元件
- `assets/` — 放你的素材(影片 my-footage.mp4、字型 fonts)
- `hyperframes.json` — 專案設定(不用動)

---

## 你要做的就三件事

**換影片(同檔名)→ 貼 SRT 給 Claude Code(它會照風格生成)→ preview → render。**

有問題隨時問老師。祝你做出很棒的動畫!
