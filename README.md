# Markdown Editor Pro

> A single-file, zero-install Markdown editor that runs entirely in your browser — with native file system access, dual preview, three themes, and a serious focus on real-world writing workflows.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![No Build](https://img.shields.io/badge/build-none-brightgreen.svg)
![Single File](https://img.shields.io/badge/single--file-HTML-orange.svg)

---

## ✨ Highlights

- **Single HTML file. No npm, no build, no server.** Just open it in a Chromium-based browser and you're editing.
- **True file system integration** via the File System Access API — open a folder, edit any `.md` inside, hit `Ctrl+S`, the file on disk is updated. No download dance.
- **Side-by-side dual preview** — render the file you're editing on the left, and load *any other* `.md` file on the right for reference. Synchronized scrolling optional.
- **Drag & drop with smart routing** — in dual-preview mode, dropping a file on the left half loads it into the editor, dropping on the right half loads it into preview B.
- **Three carefully tuned themes** — Dark (Catppuccin-inspired), Light, and Warm (paper-like sepia) — each with consistent preview styling.
- **YAML front matter is rendered as a labeled card**, not as broken markdown — see your metadata at a glance instead of losing it to the parser.
- **One-click code block copy** — every fenced code block in the preview gets a hover-revealed "Copy" button with success feedback.
- **Folder explorer with live search** — open a folder once, browse the tree, type to filter, `Enter` to open the top match.

## 🎬 Quick Start

```bash
# 1. Clone
git clone https://github.com/fishforgithub/markdown-editor-pro.git
cd markdown-editor-pro

# 2. Open the HTML file in Chrome / Edge / Brave / Arc
#    (Firefox/Safari work for editing, but lose direct-save — see Browser Compatibility)
start markdown-editor_G_V2_18.html      # Windows
open  markdown-editor_G_V2_18.html      # macOS
xdg-open markdown-editor_G_V2_18.html   # Linux
```

That's it. No package install, no dev server.

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| --- | --- |
| `Ctrl` / `Cmd` + `S` | Save current file (overwrites in place when possible) |
| `Ctrl` / `Cmd` + `P` | Open sidebar and focus file search |
| `Esc` (in search) | Clear search and blur input |
| `Enter` (in search) | Open the first matching file |

## 🧰 Feature Tour

### Editor

- Toolbar with one-click insert: headings (H1–H6), bold / italic / underline / strikethrough, horizontal rule, code block, link / URL / image, table template (3×3 starter), full-screen toggle, print.
- Synchronized line numbers that auto-resize with line count and highlight the active line.
- Unsaved-change indicator (red dot next to the filename).
- File status indicator distinguishing "directly writable" (green ●) from "save-as-only" (half-circle ◐) sources.

### Preview

- Live render via [marked.js](https://marked.js.org) v15.
- **Dual-preview mode** — render the editor's buffer on the left, and pin any other `.md` file on the right.
- **Optional synchronized scrolling** between the two preview panes (proportional, debounced).
- **Full-screen preview** for distraction-free reading.
- **YAML front matter detection** — `---\n…\n---` blocks at the top of the document are rendered as a styled "YAML Front Matter" card with theme-adaptive contrast.
- **Per-block code copy** — hover over any rendered fenced code block to reveal a copy button (with `execCommand` fallback for older browsers and a 1.5 s "✅ Copied" confirmation).

### File Operations

- **Open folder** to populate the sidebar tree (uses `showDirectoryPicker`).
- **Live search** across files in the open folder, with match highlighting and a live counter (`N/M`).
- **Save in place** when the file was opened via the File System Access API.
- **Save as…** when the source can't be overwritten (e.g., dragged-in file or clipboard).
- **Drag & drop** a `.md` file anywhere into the window to load it. In dual-preview mode, the X-coordinate of the drop decides whether it lands in the editor (left) or preview B (right).
- **Authorize a base folder for preview B** to display full relative paths instead of bare filenames.
- **Copy entire Markdown to clipboard** (front matter automatically stripped).
- **Print** the rendered preview in a clean popup window.

### Themes

| Theme | Vibe | Editor BG | Preview BG |
| --- | --- | --- | --- |
| 🌙 Dark | Catppuccin-inspired | `#1e1e2e` | `#1e1e2e` |
| ☀️ Light | Clean / classic | `#ffffff` | `#ffffff` |
| 🍂 Warm | Paper / sepia | `#fefaf3` | `#fefaf3` |

Theme is persisted in `localStorage` and applied via CSS custom properties so every UI surface — toolbar, sidebar, preview, code blocks, blockquotes, even the front-matter card — switches consistently.

### Status Bar

- Live character count, line count, current filename with save-state dot, and search match count.
- Toast notifications for every meaningful action (save success, authorization, load, copy, errors) — auto-dismiss after ~2.2 s, color-coded green/red.

## 🌐 Browser Compatibility

| Feature | Chrome / Edge / Brave / Arc | Firefox / Safari |
| --- | --- | --- |
| Editing, preview, themes, drag-drop | ✅ | ✅ |
| **Open folder & in-place save** (File System Access API) | ✅ | ❌ — falls back to download / "Save As…" |
| Clipboard copy | ✅ | ✅ (with `execCommand` fallback) |

For the full editor experience — particularly the open-folder and direct-save flow — use a Chromium-based browser.

## 🛠️ Tech Stack

- **Vanilla HTML / CSS / JavaScript** — no frameworks, no bundler, no transpile step.
- **[marked.js](https://marked.js.org) 15.0.4** (loaded from CDN) for Markdown parsing.
- **File System Access API** for native open/save.
- **Clipboard API** with graceful `execCommand` fallback.

## 📁 Project Structure

```
markdown-editor-pro/
├── markdown-editor_G_V2_18.html   # The whole app — open this in a browser
├── README.md
├── LICENSE
└── .gitignore
```

## 🤝 Contributing

Issues and PRs welcome. The codebase is intentionally a single file — keep it that way unless you have a strong reason. When adding a feature:

1. Match the existing CSS-variable / theme conventions.
2. Add a toolbar button or shortcut, not a hidden gesture.
3. Update both the English and Chinese sections of this README.

## 📜 License

[MIT](./LICENSE) © Fish

---

# Markdown 編輯器 Pro（中文）

> 一份單檔、零安裝的 Markdown 編輯器，純瀏覽器執行，整合原生檔案系統、雙預覽、三主題，專為實際寫作流程設計。

## ✨ 特色亮點

- **單一 HTML 檔，無需安裝、無需 build、無需 server。** 用 Chromium 系瀏覽器打開就能寫。
- **真正的檔案系統整合**：透過 File System Access API 開啟資料夾、編輯任何 `.md`、按 `Ctrl+S` 直接覆寫硬碟上的檔案。不用再下載一份再覆蓋。
- **雙預覽並排**：左側顯示正在編輯的檔案、右側可獨立載入「任何另一份 `.md`」當參考。同步捲動可選。
- **拖放智慧分流**：雙預覽模式下，把檔案拖到左半邊載入到編輯器、拖到右半邊載入到右預覽。
- **三種精心調校的主題**：暗色（Catppuccin 風）、亮色、暖色（紙感 sepia）— 預覽樣式跟著一起變。
- **YAML Front Matter 不會被當成壞掉的 markdown** — 自動辨識並渲染成有標題的卡片，metadata 一眼看見。
- **每個程式區塊都有一鍵複製按鈕**，hover 時出現、複製成功會跳「✅ 已複製」。
- **資料夾瀏覽 + 即時搜尋**：開過一次資料夾後，側邊欄直接顯示樹狀結構，輸入即時過濾，`Enter` 開啟第一筆。

## 🎬 快速開始

```bash
# 1. Clone
git clone https://github.com/fishforgithub/markdown-editor-pro.git
cd markdown-editor-pro

# 2. 用 Chrome / Edge / Brave / Arc 打開 HTML
#   （Firefox/Safari 也能編輯，但失去直接覆寫功能 — 詳見「瀏覽器相容性」）
start markdown-editor_G_V2_18.html      # Windows
open  markdown-editor_G_V2_18.html      # macOS
xdg-open markdown-editor_G_V2_18.html   # Linux
```

就這樣。不用 npm install，不用 dev server。

## ⌨️ 快捷鍵

| 快捷鍵 | 功能 |
| --- | --- |
| `Ctrl` / `Cmd` + `S` | 儲存目前檔案（可能時直接覆寫原檔） |
| `Ctrl` / `Cmd` + `P` | 展開側邊欄並聚焦檔案搜尋 |
| 搜尋框中按 `Esc` | 清空搜尋並失焦 |
| 搜尋框中按 `Enter` | 開啟第一筆符合的檔案 |

## 🧰 功能巡禮

### 編輯區

- 工具列一鍵插入：標題（H1–H6）、粗體 / 斜體 / 底線 / 刪除線、分隔線、程式區塊、連結 / URL / 圖片、表格模板（3×3）、全螢幕、列印。
- 同步行號，會依行數自動調寬，當前行高亮。
- 未儲存提示（檔名旁紅點）。
- 檔案來源狀態指示：可直接覆寫（綠 ●）／需另存（半圓 ◐）。

### 預覽區

- 透過 [marked.js](https://marked.js.org) v15 即時渲染。
- **雙預覽模式**：左側跟編輯器同步、右側獨立載入任何 `.md`。
- **同步捲動**（比例同步、可開關）。
- **全螢幕預覽**：純粹閱讀。
- **YAML Front Matter 偵測**：開頭的 `---\n…\n---` 會被渲染成獨立的「YAML Front Matter」卡片，主題下對比都調好。
- **程式區塊複製按鈕**：hover 時出現，使用 Clipboard API 並有 `execCommand` 後備方案，1.5 秒後恢復預設文字。

### 檔案操作

- **開啟資料夾**填入側邊欄樹（`showDirectoryPicker`）。
- **即時搜尋**檔名，含結果高亮與計數（`N/M`）。
- 透過 File System Access API 開的檔案可**直接覆寫**。
- 拖放或剪貼簿來源的檔案則使用**另存新檔**。
- **拖放上傳**：把 `.md` 拖入視窗即載入。雙預覽模式下，會根據放下時的 X 座標決定進左邊還是右邊。
- **右預覽授權基準資料夾**：可顯示完整相對路徑而非僅檔名。
- **一鍵複製整份 Markdown** 到剪貼簿（自動去除 Front Matter）。
- **列印**：彈出乾淨的預覽列印視窗。

### 主題

| 主題 | 風格 | 編輯器底色 | 預覽底色 |
| --- | --- | --- | --- |
| 🌙 暗色 | Catppuccin 風 | `#1e1e2e` | `#1e1e2e` |
| ☀️ 亮色 | 經典簡約 | `#ffffff` | `#ffffff` |
| 🍂 暖色 | 紙感 sepia | `#fefaf3` | `#fefaf3` |

主題存在 `localStorage`，透過 CSS 自訂變數套用，所以工具列、側邊欄、預覽、程式區塊、引用塊、Front Matter 卡片都會一起切換。

### 狀態列

- 即時字元數、行數、檔名（含未存提示點）、搜尋符合數。
- 所有重要動作（儲存、授權、載入、複製、錯誤）都會跳 toast 提示，2.2 秒自動消失，紅綠分色。

## 🌐 瀏覽器相容性

| 功能 | Chrome / Edge / Brave / Arc | Firefox / Safari |
| --- | --- | --- |
| 編輯、預覽、主題、拖放 | ✅ | ✅ |
| **開啟資料夾＆原檔覆寫**（File System Access API） | ✅ | ❌ — 退化成下載／另存 |
| 剪貼簿複製 | ✅ | ✅（有 `execCommand` 後備） |

要完整體驗（尤其是開啟資料夾＋直接儲存），請用 Chromium 系瀏覽器。

## 🛠️ 技術組成

- **Vanilla HTML / CSS / JavaScript** — 無框架、無 bundler、無轉譯。
- **[marked.js](https://marked.js.org) 15.0.4**（CDN 載入）負責 Markdown 解析。
- **File System Access API** 處理原生開啟／儲存。
- **Clipboard API** + `execCommand` 後備方案。

## 📁 專案結構

```
markdown-editor-pro/
├── markdown-editor_G_V2_18.html   # 整個 App — 用瀏覽器打開這支
├── README.md
├── LICENSE
└── .gitignore
```

## 🤝 參與貢獻

歡迎 Issue 與 PR。整個 App 刻意維持單檔，除非有強理由請保持這個原則。新增功能時：

1. 沿用既有的 CSS 變數／主題慣例。
2. 加在工具列或快捷鍵，避免做成隱藏手勢。
3. 同時更新本 README 的中英文兩段。

## 📜 授權

[MIT](./LICENSE) © Fish
