# 食尚玩家 Brand Guideline WEB — 專案 Context

> 這份文件記錄了網頁品牌規範的現況、檔案路徑、已完成事項與待辦清單。
> 開新對話時，把這份文件貼給 AI，即可無縫接軌。

---

## 專案概覽

- **專案名稱**：食尚玩家 品牌識別規範網頁版
- **對外網址**：`https://sprightly-cobbler-7bcdd2.netlify.app`（Netlify Drop 靜態托管）
- **更新方式**：修改 HTML → 複製到 deploy 資料夾 → 整個 deploy 資料夾拖曳到 Netlify Drop

---

## 核心檔案路徑

| 用途 | 路徑 |
|------|------|
| **主要編輯檔案** | `/Users/ono/Desktop/ono/食尚玩家/食尚玩家/Guideline/web/食尚玩家_Brand_Guideline_WEB_v4.html` |
| **Deploy 資料夾** | `/Users/ono/Desktop/ono/食尚玩家/食尚玩家/Guideline/web/食尚玩家_deploy/` |
| **Deploy HTML** | `食尚玩家_deploy/Guideline/web/食尚玩家_Brand_Guideline_WEB_v4.html` |
| **圖片資源** | `食尚玩家_deploy/web-assets/images/` |
| **連結圖示** | `食尚玩家_deploy/Guideline/link/`（玩行動力.png、路探索.png、parther logo.png）|

### Sync 指令（修改完必跑）
```bash
cp "/Users/ono/Desktop/ono/食尚玩家/食尚玩家/Guideline/web/食尚玩家_Brand_Guideline_WEB_v4.html" \
   "/Users/ono/Desktop/ono/食尚玩家/食尚玩家/Guideline/web/食尚玩家_deploy/Guideline/web/"
```

> **注意**：Source HTML 的 `../../web-assets/` 路徑在本機直接開啟時圖片會 404，這是正常的。
> 必須用 deploy 資料夾內的 HTML 預覽，或上傳 Netlify 後才能看到圖片。

---

## 技術架構

- **單一 HTML 檔案**，內嵌全部 CSS + JS，無外部框架
- **字型**：`@font-face` LINESeedTW WOFF2（4 weights：400/500/700/900）+ Google Sans Flex（CDN）
- **CSS Custom Properties**：`--orange`、`--tc`（中文字型）、`--en`（英文字型）、`--pad-y`、`--r`（border-radius）
- **RWD 斷點**：`max-width: 1024px`（手機/平板）
- **圖片路徑**：`../../web-assets/images/檔案名.jpg`

---

## 已完成項目

### 版面與 CSS
- [x] Typography 展示區（`.type-zh`）改為 LINESeed Bold（font-weight: 700）
- [x] 橫式 Logo 手機版壓縮視窗不再異常放大（`min(78%, 360px)`）
- [x] 直式 Logo 手機版尺寸修正（`max-height: 165px; max-width: 67%`）
- [x] 圖片統一 `aspect-ratio: 4/3 + object-fit: cover`

### 重建為 HTML（原本是 PDF 截圖）
- [x] **p16 Text on Color**（1-8）— 4 欄色卡 grid，含好/不好對比
- [x] **0-1 Brand Essence**（品牌精神）— 3 欄 + 箭頭 grid

### Netlify Deploy
- [x] 建立 `食尚玩家_deploy/` 資料夾結構（含 index.html redirect）
- [x] 修復掉圖問題（補上 `Guideline/link/` 3 個 icon 檔案）
- [x] 圖片壓縮：`playful.jpg`（186KB）、`imaginative.jpg`（174KB）、`real.jpg`（171KB）

---

## 待辦清單

- [ ] **GitHub 設定**：在 github.com 建立帳號 → 新增 repo → 連接 Netlify 自動部署
- [ ] **p17 Logo Color**（1-5）— 可重建為 HTML（有 SVG logo 可用 + CSS 背景色）
- [ ] **p13 Minimum Size**（1-3）— 可重建為 HTML
- [ ] **Brand Personality（0-2）**— 確認是否需要對齊 PDF 版本
- [ ] **直式 Logo 手機大小確認**：目前 165px / 67%，使用者尚未確認是否滿意

---

## 頁面結構（sections）

| Section ID | 頁面內容 | 實作方式 |
|------------|----------|----------|
| `sec-0-1` | Brand Essence（品牌精神） | HTML（已重建） |
| `sec-0-2` | Brand Personality（品牌個性） | HTML |
| `sec-1-1` | Logo 主標誌 | HTML |
| `sec-1-2` | Logo 中英文版本 | HTML |
| `sec-1-3` | Minimum Size | 截圖（p13.jpg） |
| `sec-1-4` | Logo 使用規範 | HTML |
| `sec-1-5` | Logo Color | 截圖（p17.jpg）→ 待重建 |
| `sec-1-6` | Don'ts | 截圖（p14.jpg）— 框線在圖內，不改 |
| `sec-1-7` | 字體規範 | HTML |
| `sec-1-8` | Text on Color | HTML（已重建） |

---

## 重要設計決策記錄

1. **Don'ts 外框**：`.dont-cell` 邊框在截圖 `p14.jpg` 圖片內，非 CSS 控制，暫不修改
2. **路徑策略**：所有圖片用 `../../web-assets/` 相對路徑，只在 deploy 目錄結構下正確
3. **本機預覽**：必須用 `food_deploy/Guideline/web/HTML` 開啟，不能直接開 source 檔
4. **箭頭置中**：Essence 箭頭用 `padding-top: clamp(60px, 6.5vw, 90px)` 對齊圖片中段

---

## CSS 快速參考（關鍵 class）

```css
/* 品牌精神三欄 */
.essence-grid { display:grid; grid-template-columns:1fr auto 1fr auto 1fr; }
.essence-col img { aspect-ratio:4/3; object-fit:cover; }
.essence-arrow { padding-top:clamp(60px,6.5vw,90px); }

/* Text on Color */
.toc-grid { display:grid; grid-template-columns:repeat(4,1fr); }
.toc-card { border-radius:var(--r); padding:24px 20px; min-height:160px; }

/* 直式 Logo 手機 */
@media(max-width:1024px) {
  .combo .item.vertical img { max-height:165px; max-width:67%; }
}
```
