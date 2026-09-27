# 屏北高中 Agent 基本功懶人包 #12：連接 Obsidian

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A11 給它一個會長大的記憶**（三層結構、每週知識重整）；接在 11 NotebookLM 之後
> 使用的轉接頭：[MCPVault](https://github.com/bitbonsai/mcpvault)（社群開發，開源）；做法參考三師爸 Sense Bar Codex 懶人包 #03
> 狀態：🟡 **已依官方與原作資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

讓 AI 讀寫你的 Obsidian 筆記庫，變成你的「第二大腦」：

| 你說 | AI 會做 |
|---|---|
| 「在我的筆記庫找所有提到『差異化教學』的筆記，整理成一頁重點」 | 搜尋全庫、讀相關筆記、整理 |
| 「把剛剛 NotebookLM 產生的學習指引存成一篇筆記，放在『備課』資料夾」 | 建立新筆記，保留格式 |
| 「幫這週新增的筆記補上標籤」 | 讀筆記、只改標籤欄位，不動內文 |

**Obsidian 不用開著也能用**：這個轉接頭直接讀寫筆記檔案，不需要裝任何 Obsidian 外掛、不需要金鑰。

### 其實有更簡單的做法

如果你**只在同一個資料夾裡工作**，直接在 Codex 把筆記庫資料夾開成專案，AI 本來就讀寫得到，不用裝這包。
這包的用處是：**不管你在哪個專案資料夾工作**，AI 都能去翻你的筆記庫、把成果存回去。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 會問你**筆記庫在哪個資料夾**（它會先幫你找，你只要確認是不是那一個）
4. AI 要動到電腦時會跳出確認，**看一眼、按同意**
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/12-MCP-Obsidian.md
照其中「給 AI Agent 的執行步驟」，幫我把 Obsidian 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**還沒有 Obsidian 筆記庫？** AI 會問你要不要幫你裝 Obsidian、在「文件」裡建一個新的筆記庫資料夾。

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
用 obsidian 工具告訴我，我的筆記庫有幾篇筆記、最上層有哪些資料夾。
```

再試一次寫入（會在筆記庫裡建一個測試資料夾）：

```text
在我的筆記庫建立「AI測試/連線測試.md」，內容寫「Codex 連線成功」和今天日期，建好後讀回來給我看。
```

確認沒問題後，可以請 AI 把「AI測試」資料夾刪掉，或自己在 Obsidian 裡刪。

---

## 安全提醒

- **筆記庫如果放在雲端硬碟**（Google Drive、OneDrive），AI 的每一個修改都會同步到你所有電腦。剛開始先叫它**只在一個資料夾裡寫**，例如「AI 產出」。
- AI 能讀到筆記庫的**全部內容**。輔導紀錄、學生個資這類筆記，請不要放在同一個筆記庫。
- 大量修改前，先說「先列出你要改哪些檔案，我確認後再改」（教材 A6：接得上不代表什麼都讓它動）。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（安裝、修改設定檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **筆記庫路徑一定要老師確認**，不可自己挑一個就寫進設定。
> 6. 安裝過程中**不要讀取或修改筆記內容**（驗收時的「AI測試」資料夾除外）；改 `config.toml` 前一定先備份。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**（例如不要改裝需要 Local REST API 外掛的其他 Obsidian MCP）。
> 8. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
node --version
Test-Path "$env:APPDATA\npm\mcpvault.cmd"
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.obsidian\]' -Quiet
```

| 項目 | 狀態 |
|---|---|
| Node.js | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查](00-環境檢查與基礎工具.md)，本包停止） |
| mcpvault 已安裝 | `True`／`False` |
| Codex 設定已加入 | `True`／`False` |

三項都 `True` → 跳到步驟六驗證。

### 步驟二：找出筆記庫（只讀，直接執行）

Obsidian 的筆記庫是**裡面有 `.obsidian` 資料夾**的資料夾。在常見位置找（只找 4 層，避免掃太久）：

```powershell
$roots = @(
    [Environment]::GetFolderPath('MyDocuments'),
    "$env:USERPROFILE\Desktop",
    "$env:USERPROFILE\OneDrive",
    "$env:USERPROFILE\我的雲端硬碟",
    "G:\我的雲端硬碟"
) | Where-Object { Test-Path $_ }
Get-ChildItem "$env:USERPROFILE\我的雲端硬碟 (*" -Directory -ErrorAction SilentlyContinue | ForEach-Object { $roots += $_.FullName }
$roots | ForEach-Object {
    Get-ChildItem $_ -Directory -Recurse -Depth 4 -Filter ".obsidian" -Force -ErrorAction SilentlyContinue
} | ForEach-Object { $_.Parent.FullName } | Sort-Object -Unique
```

把找到的路徑列給老師，問：「**你的 Obsidian 筆記庫是哪一個？**」

- 找到一個以上 → 請老師選
- 一個都沒有 → 問老師：「要我幫你安裝 Obsidian，並在『文件』建立一個叫『我的第二大腦』的新筆記庫嗎？」
  - 老師同意（要老師同意）：
    ```powershell
    winget install --id Obsidian.Obsidian -e --accept-source-agreements --accept-package-agreements
    $vault = Join-Path ([Environment]::GetFolderPath('MyDocuments')) '我的第二大腦'
    New-Item -ItemType Directory -Force $vault | Out-Null
    ```
    並告訴老師：「之後打開 Obsidian，選『開啟資料夾作為筆記庫』，選『文件\我的第二大腦』。」
  - 老師不要 → 本包停止，回報原因

### 步驟三：安裝 mcpvault（要老師同意）

```powershell
npm.cmd install -g @bitbonsai/mcpvault
Test-Path "$env:APPDATA\npm\mcpvault.cmd"
```

> 為什麼不用 `npx`：Codex 的沙箱常寫不進 npm 快取（`EPERM ... npm-cache`），npx 冷啟動也常超過 Codex 預設的 10 秒啟動時限（三師爸實測踩過）。
> PowerShell 回「已停用指令碼執行」時，確認用的是 `npm.cmd` 不是 `npm`。

### 步驟四：先單獨測一次轉接頭（只讀，直接執行）

把 `$vault` 換成老師確認的路徑：

```powershell
$vault = '<老師確認的筆記庫路徑>'
'{"jsonrpc":"2.0","id":1,"method":"tools/list"}' | & "$env:APPDATA\npm\mcpvault.cmd" $vault
```

看得到 `read_note`、`write_note`、`search_notes` 等工具名稱就正常。沒輸出或報錯 → 停下來回報，不要進步驟五。

### 步驟五：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再附加到 `config.toml` 最後面（已有 `[mcp_servers.obsidian]` 就不要重複加；路徑不同時先問老師要換成哪個）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$cmd = "$env:APPDATA\npm\mcpvault.cmd"
$block = @"

# 屏北高中懶人包 #12：Obsidian 筆記庫（MCPVault，直接讀寫筆記檔案，不需要外掛與金鑰）
[mcp_servers.obsidian]
command = '$cmd'
args = ['$vault']
startup_timeout_sec = 30
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 路徑用 TOML **單引號字串**，反斜線不用加倍，中文與空白也沒問題；**路徑裡不能有單引號**（有的話停下來回報）。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面，並提醒老師**之後重新套用 NMK 連線設定會蓋掉這段，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add obsidian --scope user -- cmd /c "$env:APPDATA\npm\mcpvault.cmd" "$vault"
```

Claude Code 也可以不裝 MCP：把筆記庫加進 `settings.json` 的 `additionalDirectories`，直接用讀檔工具讀寫。

### 步驟六：驗證

**剛改完設定**：這個對話還看不到 obsidian 工具。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一三項都 `True`
2. 用 obsidian 工具的 `get_vault_stats` 回報筆記數量
3. 看不到工具 → 請老師到 Codex **設定 → MCP servers** 看 `obsidian` 是否啟用、有無錯誤訊息
4. 寫入測試交給老師照「裝好之後：驗收」做，不要在安裝流程裡自己寫筆記

### 步驟七：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 12 Obsidian（YYYY-MM-DD HH:MM）

- mcpvault：已安裝（版本 x.x.x）/ 已補裝 / 失敗
- 筆記庫路徑：<路徑>（是否在雲端硬碟：是／否）
- Codex 設定：已加入 / 失敗
- 讀取測試：成功（N 篇筆記）/ 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟八：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| Obsidian 轉接頭 | ✅／❌ |
| 筆記庫 | ✅ <資料夾名稱>／❌ |
| Codex 設定 | ✅／❌ |
| 連線測試 | ✅ 共 N 篇筆記／⚠️ 要重開後再貼一次／❌ |

筆記庫在雲端硬碟時，要特別提醒老師：「AI 的修改會同步到你所有電腦，先讓它只寫在一個資料夾裡。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Obsidian 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #12` 那一段（先備份）
2. `npm.cmd uninstall -g @bitbonsai/mcpvault`
3. 筆記庫本身**完全不要動**

## 來源與查證（2026-09-27）

- MCPVault（npm `@bitbonsai/mcpvault` 0.16.0，不需 Obsidian 外掛）：<https://github.com/bitbonsai/mcpvault>
- 三師爸 Sense Bar Codex 懶人包 #03（全域安裝＋完整路徑、npx 沙箱踩坑）：<https://github.com/mathruffian-dot/codex-lazy-packs>
- 另一條路（本包不採用）：Obsidian 社群外掛 Local REST API 自 v5 起內建 MCP，但 **Obsidian 必須開著**、要設金鑰，對研習太複雜：<https://github.com/coddingtonbear/obsidian-local-rest-api>
- Codex MCP 設定：<https://learn.chatgpt.com/docs/extend/mcp>
