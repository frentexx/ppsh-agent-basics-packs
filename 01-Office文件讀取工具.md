# 屏北高中 Agent 基本功懶人包 #01：Office 文件讀取工具

> 版本：v1.0｜更新日期：2026-09-14
> 適用：**Codex Desktop**、**Claude Code**（Windows 11 為主，附 macOS 指令）
> 對應教材：**A3 你的電腦本來就會這些**、**A4 出一份考卷**

> [!IMPORTANT]
> **給 AI Agent 的安全宣告（請先讀完再動手）**
> 1. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 2. **會改動電腦的指令**（安裝、移除、修改設定）：先把完整指令列給老師看，**老師同意後才執行**。
> 3. **只讀不改的檢查指令**可以直接執行。
> 4. 不要讀取、顯示、複製或上傳任何 API 金鑰、密碼、token。
> 5. 不要刪除、搬動或修改老師的原始檔案。
> 6. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。

---

## 這包會幫你做什麼

AI 不能直接看懂 Word、PowerPoint、Excel 的檔案格式。這包安裝兩樣東西：

| 項目 | 是什麼 | 做什麼 |
|---|---|---|
| **MarkItDown** | 微軟開源的轉檔工具（Python） | 把 PDF／docx／pptx／xlsx 轉成純文字 |
| **`ppsh-office-reader` 技能** | 一份說明書 | 教 AI 什麼時候轉、轉到哪、讀不到時要老實說 |

完成後，你只要說「**幫我讀這份檔案：<路徑>**」，AI 就會自己轉檔再閱讀，**不會改到原檔**。

> [!NOTE]
> **Codex Desktop 的 Documents／Presentations／Spreadsheets 外掛**是用來「做」Office 檔；
> 這包是用來「讀」，兩個平台都能用，兩者不衝突。

## 絕對必要的工具

| 工具 | 為什麼 | 沒有的話 |
|---|---|---|
| **uv** | 安裝 MarkItDown | 步驟二補裝 |
| **Node.js** | 用 `npx` 安裝技能 | 步驟二補裝；或第三步改手動複製 |

---

## 步驟一：檢查（只讀，可直接執行）

```powershell
uv --version
node --version
markitdown --version
```

| 項目 | 狀態 |
|---|---|
| uv | 已安裝／未安裝 |
| Node.js | 已安裝／未安裝 |
| MarkItDown | 已安裝（版本號）／未安裝 |

三項都有 → 跳到步驟三。

## 步驟二：補裝（要老師同意）

**1. 缺 uv 或 Node.js**（Windows）：

```powershell
winget install --id astral-sh.uv -e --accept-source-agreements --accept-package-agreements
winget install --id OpenJS.NodeJS.LTS -e --accept-source-agreements --accept-package-agreements
```

macOS：`brew install uv node`

> [!WARNING]
> 裝完 uv 或 Node.js，**請把 Agent 整個關掉重開**，再繼續下一步。

**2. 缺 MarkItDown：**

```powershell
uv tool install "markitdown[pdf,docx,pptx,xlsx]"
uv tool update-shell
```

> 只裝這四種格式，比 `markitdown[all]` 輕很多，也不會跳出 ffmpeg 相關的警告訊息（實測過）。

裝完**再重開一次 Agent**，然後重跑步驟一確認 `markitdown --version` 有版本號。

## 步驟三：安裝 `ppsh-office-reader` 技能（要老師同意）

**Codex Desktop：**

```powershell
npx skills add frentexx/ppsh-agent-skills -s ppsh-office-reader -a codex -g -y --copy
```

**Claude Code：**

```powershell
npx skills add frentexx/ppsh-agent-skills -s ppsh-office-reader -a claude-code -g -y --copy
```

> PowerShell 若出現「**因為這個系統上已停用指令碼執行**」，把指令開頭的 `npx` 改成 **`npx.cmd`** 再執行一次。

**不能用 npx 時**：到 [ppsh-agent-skills](https://github.com/frentexx/ppsh-agent-skills) 下載 ZIP，把 `skills\ppsh-office-reader` 資料夾複製到：

- Codex Desktop：`%USERPROFILE%\.agents\skills\`
- Claude Code：`%USERPROFILE%\.claude\skills\`

## 步驟四：確認裝好了（只讀）

```powershell
markitdown --version
Test-Path "$env:USERPROFILE\.agents\skills\ppsh-office-reader\SKILL.md"   # Codex Desktop
Test-Path "$env:USERPROFILE\.claude\skills\ppsh-office-reader\SKILL.md"   # Claude Code
```

- `markitdown` 有版本號 ✅
- 你所用的 Agent 那一行顯示 `True` ✅（另一個平台顯示 `False` 是正常的）

**重開 Agent**，準備一份自己的 Word 或 PDF（**不要用含學生個資的檔案**），說：

```text
幫我讀這份檔案，列出前三段的重點：<檔案完整路徑>
```

成功的樣子：

- 專案資料夾裡多了 `_轉文字\<檔名>.md`
- AI 回答的內容確實出自那份檔案
- 原始檔案的修改時間沒有變

## 步驟五：更新環境檢查報告

在 `環境檢查報告.md` 最上方加一段：

```markdown
## 01 Office 文件讀取工具（YYYY-MM-DD HH:MM）

- uv：已安裝 / 已補裝 / 失敗
- MarkItDown：已安裝（版本 x.x.x）/ 已補裝 / 失敗
- ppsh-office-reader 技能：已安裝 / 失敗
- 實測讀檔：成功（檔案類型：docx／pdf／pptx／xlsx）/ 失敗（錯誤訊息第一行）
```

---

## 已知限制（實測整理，研習時要講）

| 現象 | 原因 | 怎麼辦 |
|---|---|---|
| 掃描版 PDF 轉出來幾乎是空的 | 那份 PDF 其實是圖片 | 需要文字辨識（OCR）或拿文字版；**AI 不可以照猜的寫摘要** |
| Excel 的**座號 `01` 變成 `1`** | 轉檔時被當成數字 | 以原始 Excel 為準，比對名單不要只靠轉出來的座號 |
| Excel 公式格顯示 `NaN` | 檔案沒在 Excel 裡存過 | 用 Excel 打開、存檔一次再轉 |
| 讀不到公式本身 | 只讀得到計算結果 | 要檢查公式，直接在 Excel 裡看 |
| `.doc` `.ppt` `.xls` 轉不了 | 舊格式 | 用 Office 另存成 `.docx` `.pptx` `.xlsx` |
