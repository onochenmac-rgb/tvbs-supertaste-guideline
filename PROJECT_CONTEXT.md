# 食尚玩家 Brand Guideline WEB — 專案 Context

> 這份文件記錄了網頁品牌規範的現況、檔案路徑、已完成事項與待辦清單。
> 開新對話時，把這份文件貼給 AI，即可無縫接軌。

---

## 專案概覽

- **專案名稱**：食尚玩家 品牌識別規範網頁版
- **對外網址**：`https://onochenmac-rgb.github.io/tvbs-supertaste-guideline/`（GitHub Pages）
- **GitHub Repo**：`https://github.com/onochenmac-rgb/tvbs-supertaste-guideline`（Private）
- **更新方式**：Claude 修改 HTML → Sync 指令 → commit + push → 網站自動更新

---

## 核心檔案路徑

| 用途 | 路徑 |
|------|------|
| **主要編輯檔案** | `/Users/ono/Desktop/ono/食尚玩家/食尚玩家/Guideline/web/食尚玩家_Brand_Guideline_WEB_v1.html` |
| **對外 HTML** | `docs/index.html`（由 Sync 指令自動產生，勿直接編輯） |
| **圖片資源** | `docs/web-assets/images/` |
| **連結圖示** | `docs/Guideline/link/`（玩行動力.png、路探索.png、parther logo.png）|

### Sync 指令（修改完必跑，Claude 會自動執行）
```bash
sed 's|../../web-assets/|web-assets/|g; s|\.\./link/|Guideline/link/|g' \
  "食尚玩家_Brand_Guideline_WEB_v1.html" > "docs/index.html"
```

### Deploy 指令（Sync 完後執行）
```bash
git add -A && git commit -m "更新內容" && git push
```

---

## 技術架構

- **單一 HTML 檔案**，內嵌全部 CSS + JS，無外部框架
- **字型**：`@font-face` LINESeedTW WOFF2（4 weights：400/500/700/900）+ Google Sans Flex（CDN）
- **CSS Custom Properties**：`--orange`、`--tc`（中文字型）、`--en`（英文字型）、`--pad-y`、`--r`（border-radius）
- **RWD 斷點**：`max-width: 1024px`（手機/平板）
- **圖片路徑**（source 檔）：`../../web-assets/images/檔案名.jpg`
- **Logo**：SVG 已移除，全部使用 PNG

---

## 已完成項目

### 版面與 CSS
- [x] Typography 展示區（`.type-zh`）改為 LINESeed Bold（font-weight: 700）
- [x] 橫式 Logo 手機版壓縮視窗不再異常放大（`min(78%, 360px)`）
- [x] 直式 Logo 手機版尺寸修正（`max-height: 165px; max-width: 67%`）
- [x] 圖片統一 `aspect-ratio: 4/3 + object-fit: cover`
- [x] Logo SVG 全部替換為 PNG，SVG 從 git 歷史記錄中清除

### 重建為 HTML（原本是 PDF 截圖）
- [x] **p16 Text on Color**（1-8）— 4 欄色卡 grid，含好/不好對比
- [x] **0-1 Brand Essence**（品牌精神）— 3 欄 + 箭頭 grid

### GitHub 設定
- [x] 建立 Private repo：`tvbs-supertaste-guideline`
- [x] SSH 金鑰設定完成
- [x] GitHub Pages 啟用（從 `docs/` 資料夾部署）

---

## 待辦清單

- [ ] **p17 Logo Color**（1-5）— 可重建為 HTML（CSS 背景色）
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
2. **路徑策略**：source 檔用 `../../web-assets/`，Sync 時自動轉換為 `web-assets/`
3. **Logo 保護**：SVG 已從 repo 及 git 歷史中清除，僅保留 PNG
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
