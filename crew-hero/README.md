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
https://cdn.jsdelivr.net/gh/rindytsan/lottie@main/crew-hero/mobile-zh.html
```

容器比例要設對，否則會留邊（不會裁切）。

不吃外部網址的話，改用「嵌入 HTML 程式碼」：

```html
<iframe src="https://cdn.jsdelivr.net/gh/rindytsan/lottie@main/crew-hero/mobile-zh.html"
        style="width:100%;aspect-ratio:1440/1800;border:0"
        loading="lazy"></iframe>
```

## 特性

- 18 秒無縫循環、自動播放、無聲
- 四角 20px 圓角，圓角外透明
- 文字是真的 DOM 文字，任意解析度都銳利
- 圖片內嵌並降到顯示尺寸 2 倍（2.85 MB → 1.51 MB）
- GSAP 內嵌，只有 Google Fonts 需要連外
- 切分頁暫停、切回續播

## 更新

原始碼在 `~/Rindy_Coding/videos/crew-hero`，改完重跑：

```bash
node build-standalone.mjs compositions/mobile.html    mobile-zh  1440 1800 mobile    20
node build-standalone.mjs compositions/mobile-en.html mobile-en  1440 1800 mobile-en 20
node build-standalone.mjs index.html                  desktop-zh 1920 1080 main      20
node build-standalone.mjs compositions/desktop-en.html desktop-en 1920 1080 main-en  20
```

最後一個參數是圓角 px。覆蓋本資料夾後 push，**網址不變**，Wix 端不用改。
jsDelivr 有快取（約 12 小時），要立刻生效就把網址的 `@main` 換成 commit SHA。
