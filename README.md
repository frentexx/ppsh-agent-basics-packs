# 屏北高中 Agent 基本功懶人包

> 屏北高中教師研習用的 AI Agent 安裝與設定懶人包。
> **每份 MD 檔都寫給 AI 讀**——把檔案交給你的 AI Agent，它會照步驟檢查、補裝、再檢查，最後產出一份環境檢查報告。
>
> ✅ 適用：**Codex Desktop**、**Claude Code**（Windows 11 為主，附 macOS 指令）

技能本體放在姊妹 repo：👉 **[屏北高中 Agent Skill 懶人包](https://github.com/frentexx/ppsh-agent-skills)**

---

## 怎麼用：貼一句話給你的 AI Agent

```text
這是屏北高中 Agent 基本功懶人包 https://github.com/frentexx/ppsh-agent-basics-packs
請讀取 README 列出所有懶人包，問我要做哪幾個，再依編號順序執行。
每一個會改動電腦的指令，先給我看、經我同意再執行。
```

只想做其中一包，把網址換成那一份 MD 檔的網址即可。

## 研習前建議順序

```
00 環境檢查  →  01 Office 讀取工具  →  02 初始化／開工／收工技能  →  03 教材產出技能
```

四包做完，會得到一份 `環境檢查報告.md`。研習現場卡關時，把這份報告給助教看。

> **03 有兩個東西要在研習前先裝好**：**Chrome** 和 **Python 套件**。
> Python 套件那一行可能要跑好幾分鐘，**不要留到現場再裝**。

---

## 懶人包清單

| 編號 | 名稱 | 做什麼 | 對應教材 | 狀態 |
|---|---|---|---|---|
| 00 | [環境檢查與基礎工具](00-環境檢查與基礎工具.md) | Git、GitHub CLI、Node.js、uv；Codex 五個必裝外掛 | 研習前準備 | ✅ |
| 01 | [Office 文件讀取工具](01-Office文件讀取工具.md) | MarkItDown ＋ `ppsh-office-reader` 技能，讀 PDF／Word／PPT／Excel | A3、A4 | ✅ |
| 02 | [專案初始化、開工、收工技能](02-專案初始化開工收工技能.md) | 三個技能，換電腦、開新對話都接得上 | A5 | ✅ |
| 03 | [教材產出技能包](03-教材產出技能包.md) | 三個技能：圖卡（PNG）、可編輯簡報（.pptx）、網頁簡報（.html）。**都不需要 API 金鑰** | 速成版 S2 | ✅ |
| 04–09 | （保留） | 之後的基礎工具與技能 | | |
| 10 | [連接 Padlet](10-MCP-Padlet.md) | Padlet 貼文整理與建立 | A6 | ⬜ 骨架 |
| 11 | [連接 NotebookLM](11-MCP-NotebookLM.md) | 備課包、講座摘要 | A7 | ⬜ 骨架 |
| 12 | [連接 Obsidian](12-MCP-Obsidian.md) | 第二大腦（接在 NotebookLM 之後：筆記本整理完的知識存進自己的筆記庫） | A11 | ⬜ 骨架 |
| 13 | [連接 Wordwall](13-MCP-Wordwall.md) | 教材轉遊戲活動 | A8 | ⬜ 骨架 |
| 14 | [連接 GitHub](14-MCP-GitHub.md) | HTML 簡報部署到 GitHub Pages | A9 | ⬜ 骨架 |
| 15 | [連接 Canva](15-MCP-Canva.md) | 簡報與文宣設計 | （教材尚未涵蓋） | ⬜ 骨架 |
| 16 | [連接 Kahoot](16-MCP-Kahoot.md) | 課中概念辨識測驗 | （教材尚未涵蓋） | ⬜ 骨架 |

**⬜ 骨架**＝編號與用途已定，安裝步驟尚未實測，**請勿照著安裝**。

## 編號規則（新增懶人包時）

| 範圍 | 放什麼 |
|---|---|
| **00–09** | 基礎工具與技能（研習前一定要做的） |
| **10–49** | MCP 與外部服務連線，**依研習的使用順序排列**（大致跟著教材單元，NotebookLM → Obsidian 刻意相連） |
| **50–** | 保留 |

- 新增時取該範圍的**下一個空號**，**不要重排既有編號**（老師手上的舊連結才不會失效）
- 真的要插在兩包之間，用小數點：`10.5-MCP-xxx.md`
- 每份懶人包都要有：**給 Agent 的安全宣告**、**檢查 → 補裝 → 再檢查**、**環境檢查報告段落**

---

## 安全原則（每一份懶人包都遵守）

1. 只安裝文件列出的項目
2. 會改動電腦的指令，先給老師看、同意後才執行
3. AI 不碰任何金鑰、密碼；登入由老師自己操作
4. 不刪除、不搬動老師的檔案

## 授權

MIT License。架構參考 [mathruffian-dot/codex-lazy-packs](https://github.com/mathruffian-dot/codex-lazy-packs)（MIT）。
