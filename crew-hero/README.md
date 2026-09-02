# Raccoon AI Crew — hero 動畫

四支自帶一切的 HTML，給 Wix 的 iFrame 嵌入用。**繞過 Wix 的影片轉檔階梯**，所以手機上不會糊。

| 檔案 | 版面 | 容器比例 |
|---|---|---|
| `mobile-zh.html`  | 手機中文 | **4:5**（1440×1800）|
| `mobile-en.html`  | 手機英文 | 4:5 |
| `desktop-zh.html` | 桌機中文 | **16:9**（1920×1080）|
| `desktop-en.html` | 桌機英文 | 16:9 |

## Wix 放法

**新增 → 嵌入程式碼 → 嵌入網站**，填 jsDelivr 網址：

```
https://rindytsan.github.io/lottie/crew-hero/mobile-zh.html
```

容器比例要設對，否則會留邊（不會裁切）。

不吃外部網址的話，改用「嵌入 HTML 程式碼」：

```html
<iframe src="https://rindytsan.github.io/lottie/crew-hero/mobile-zh.html"
        style="width:100%;aspect-ratio:1440/1800;border:0"
        loading="lazy"></iframe>
```

## 特性

- 18 秒無縫循環、自動播放、無聲
- 四角 20px 圓角，圓角外透明
- 文字是真的 DOM 文字，任意解析度都銳利
- 圖片放在 assets/，可被瀏覽器快取（HTML 僅 110 KB，圖片 1.13 MB 四支共用）
- GSAP 內嵌；圖片與 Google Fonts 需連外
- 圖片載齊且尺寸穩定才顯示，不會閃
- 切分頁暫停、切回續播

## 更新

原始碼在 `~/Rindy_Coding/videos/crew-hero`，改完重跑：

```bash
node build-standalone.mjs compositions/mobile.html    mobile-zh  1440 1800 mobile    20 external
node build-standalone.mjs compositions/mobile-en.html mobile-en  1440 1800 mobile-en 20 external
node build-standalone.mjs index.html                  desktop-zh 1920 1080 main      20 external
node build-standalone.mjs compositions/desktop-en.html desktop-en 1920 1080 main-en  20 external
```

倒數第二個參數是圓角 px，最後一個是 `inline`（圖片內嵌）或 `external`（圖片獨立成檔）。
**四支目前都用 `external`** —— 圖片會寫進 `standalone/assets/`，記得連同 `crew-hero/assets/` 一起覆蓋。
覆蓋本資料夾後 push，**網址不變**，Wix 端不用改。
GitHub Pages 建置約 1 分鐘，之後網址就是最新的。

> **不要用 jsDelivr。** 它把 `.html` 當 `text/plain` 送（安全政策），
> iframe 會把原始碼當純文字印出來，不會渲染。
