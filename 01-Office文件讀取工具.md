# 屏北高中 Agent 基本功懶人包 #01：Office 文件讀取工具

> 版本：v1.1｜更新日期：2026-09-27
> 適用：**Codex Desktop**、**Claude Code**（Windows 11 為主，附 macOS 指令）
> 對應教材：**A3 你的電腦本來就會這些**、**A4 出一份考卷**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

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

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做四件事：

1. 打開 **Codex Desktop** 或 **Claude Code**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 說「請重開」時，把 Codex／Claude Code **整個關掉再打開**，然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/01-Office文件讀取工具.md
照其中「給 AI Agent 的執行步驟」，幫我把這一包需要的工具和技能全部裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：讀一份檔案驗收

重開 Agent，準備一份自己的 Word 或 PDF（**不要用含學生個資的檔案**），跟它說：

```text
幫我讀這份檔案，列出前三段的重點：<檔案完整路徑>
```

> 不知道完整路徑？在檔案總管對檔案按右鍵 →「**複製路徑**」，再貼進來。

成功的樣子：

- 專案資料夾裡多了 `_轉文字\<檔名>.md`
- AI 回答的內容確實出自那份檔案
- 原始檔案的修改時間沒有變

---

## 已知限制（實測整理，研習時要講）

| 現象 | 原因 | 怎麼辦 |
|---|---|---|
| 掃描版 PDF 轉出來幾乎是空的 | 那份 PDF 其實是圖片 | 需要文字辨識（OCR）或拿文字版；**AI 不可以照猜的寫摘要** |
| Excel 的**座號 `01` 變成 `1`** | 轉檔時被當成數字 | 以原始 Excel 為準，比對名單不要只靠轉出來的座號 |
| Excel 公式格顯示 `NaN` | 檔案沒在 Excel 裡存過 | 用 Excel 打開、存檔一次再轉 |
| 讀不到公式本身 | 只讀得到計算結果 | 要檢查公式，直接在 Excel 裡看 |
| `.doc` `.ppt` `.xls` 轉不了 | 舊格式 | 用 Office 另存成 `.docx` `.pptx` `.xlsx` |
| 說「幫我讀這份檔案」沒反應 | 裝完沒重開 Agent | 整個關掉重開；還不行就**再貼一次安裝那段話** |

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（安裝、移除、修改設定）：照你所在 Agent 的權限確認機制取得老師同意（跳出確認讓老師按）。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. 不要讀取、顯示、複製或上傳任何 API 金鑰、密碼、token。
> 6. 不要刪除、搬動或修改老師的原始檔案。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過，不要重裝。

### 需要的工具

| 工具 | 為什麼 | 沒有的話 |
|---|---|---|
| **uv** | 安裝 MarkItDown | 步驟二補裝 |
| **Node.js** | 用 `npx` 安裝技能 | 步驟二補裝；或步驟三走路線 B（不需要 Node.js） |

### 步驟一：檢查（只讀，直接執行）

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

### 步驟二：補裝（要老師同意）

**1. 缺 uv 或 Node.js**（Windows，只裝缺的那個）：

```powershell
winget install --id astral-sh.uv -e --accept-source-agreements --accept-package-agreements
winget install --id OpenJS.NodeJS.LTS -e --accept-source-agreements --accept-package-agreements
```

macOS：`brew install uv node`

> [!WARNING]
> 剛裝好的 uv／Node.js，**這個對話還叫不到**（PATH 要重開才更新）。
> 先做步驟三的**路線 B**把技能裝好（不需要 Node.js），然後在回報中請老師**重開 Agent、再貼一次同一段話**，重開後再裝 MarkItDown。

**2. 缺 MarkItDown**（uv 叫得到才做）：

```powershell
uv tool install "markitdown[pdf,docx,pptx,xlsx]"
uv tool update-shell
```

只裝這四種格式，比 `markitdown[all]` 輕很多，也不會跳出 ffmpeg 相關的警告訊息（實測過）。
裝完 `markitdown --version` 仍叫不到，是 PATH 還沒更新——在回報中請老師重開 Agent、再貼一次同一段話。

### 步驟三：安裝 `ppsh-office-reader` 技能（要老師同意）

先判斷你是哪個 Agent，只裝到**你自己**的技能資料夾：

| 你是 | 技能資料夾（Windows） | 技能資料夾（macOS） | npx 的 `-a` |
|---|---|---|---|
| Codex Desktop | `%USERPROFILE%\.agents\skills\` | `~/.agents/skills/` | `codex` |
| Claude Code | `%USERPROFILE%\.claude\skills\` | `~/.claude/skills/` | `claude-code` |

Codex **不要用內建的 `$skill-installer`**：它會裝到 `.codex\skills\`，不是官方的個人技能資料夾。

**路線 A（有 Node.js）：**

```powershell
npx skills add frentexx/ppsh-agent-skills -s ppsh-office-reader -a <codex 或 claude-code> -g -y --copy
```

PowerShell 回「因為這個系統上已停用指令碼執行」→ 把 `npx` 改成 `npx.cmd` 重跑。

**路線 B（沒有 Node.js，或路線 A 失敗）：下載 ZIP 後複製**

```powershell
$tmp = Join-Path $env:TEMP "ppsh-agent-skills"
Invoke-WebRequest "https://github.com/frentexx/ppsh-agent-skills/archive/refs/heads/main.zip" -OutFile "$tmp.zip"
Expand-Archive "$tmp.zip" -DestinationPath $tmp -Force
$dst = "$env:USERPROFILE\.agents\skills"   # Claude Code 改成 "$env:USERPROFILE\.claude\skills"
New-Item -ItemType Directory -Force $dst | Out-Null
Copy-Item "$tmp\ppsh-agent-skills-main\skills\ppsh-office-reader" $dst -Recurse -Force
```

macOS 用 `curl -L -o` 下載、`unzip` 解壓，再 `cp -R` 到上表的資料夾。

### 步驟四：確認裝好了（只讀）

```powershell
markitdown --version
Test-Path "$env:USERPROFILE\.agents\skills\ppsh-office-reader\SKILL.md"   # Codex Desktop
Test-Path "$env:USERPROFILE\.claude\skills\ppsh-office-reader\SKILL.md"   # Claude Code
```

- `markitdown` 有版本號 ✅
- 你所屬 Agent 那一行顯示 `True` ✅（另一個平台顯示 `False` 是正常的）

### 步驟五：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有這個檔就新建）：

```markdown
## 01 Office 文件讀取工具（YYYY-MM-DD HH:MM）

- uv：已安裝 / 已補裝 / 失敗
- MarkItDown：已安裝（版本 x.x.x）/ 已補裝 / 失敗
- ppsh-office-reader 技能：已安裝 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟六：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| 轉檔工具 MarkItDown | ✅ 版本／⚠️ 要重開後再貼一次／❌ |
| 讀檔技能 ppsh-office-reader | ✅／❌ |

最後一定要明確告訴老師下一步，例如：
「請把 Codex（或 Claude Code）**整個關掉再打開**，然後照這份文件的『裝好之後：讀一份檔案驗收』試一次。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。
