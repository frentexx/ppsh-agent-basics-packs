# 屏北高中 Agent 基本功懶人包 #10：連接 Padlet

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A6 沒有 API 也連得上**；概念入門版 1-5c（MCP 轉接頭的範例）
> 使用的轉接頭：三師爸 Sense Bar 的 [padlet-mcp](https://github.com/mathruffian-dot/padlet-mcp)（MIT）
> 狀態：🟡 **已依官方與原作資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

裝好之後，你可以直接跟 AI 說：

| 你說 | AI 會做 |
|---|---|
| 「幫我開一面『光合作用』課前討論牆，分成迷思、生活應用、提問三區」 | 在你的 Padlet 開一面新牆，每區先放引導問題 |
| 「讀這面牆 <網址>，把學生回答分成正確／部分正確／迷思三類」 | 讀完整面牆，整理成表格給你 |
| 「在每張有迷思的卡片底下留一句提問，不要直接給答案」 | 逐張留言 |

---

## ⚠️ 先確認：你的 Padlet 能不能用

**這包需要 Padlet 付費方案**（個人付費版、學校版都可以）。免費帳號拿不到 API 金鑰，裝了也不能用。

檢查方法（1 分鐘）：

1. 登入 Padlet，打開 <https://padlet.com/dashboard/settings>
2. 左邊選單有沒有「**Developer（開發者）**」，裡面有沒有「**API key**」

有 → 繼續往下做；沒有 → 這包先跳過。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 會**另外跳出一個藍色小視窗**請你貼 Padlet 金鑰——金鑰只貼在那個小視窗，**不要貼進對話**
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/10-MCP-Padlet.md
照其中「給 AI Agent 的執行步驟」，幫我把 Padlet 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

### 金鑰去哪裡拿（AI 跳出小視窗時再做）

1. 打開 <https://padlet.com/dashboard/settings> → 左邊「**Developer**」
2. API key 旁邊按「**Generate**」（已經有就按複製）
3. 回到那個藍色小視窗，按右鍵貼上，按 Enter

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
用 padlet 的 whoami 確認連線，告訴我是哪個帳號。
```

看到你的 Padlet 帳號名稱就成功了。再試一次真的動作：

```text
幫我開一面叫「連線測試」的 Padlet，只要一個區段，放一張寫著「成功」的卡片，給我網址。
```

---

## 已知限制（Padlet 官方 API 的邊界，研習時要講）

| 做不到 | 怎麼辦 |
|---|---|
| 刪除、修改既有卡片 | 回 Padlet 網頁自己改 |
| 在既有的牆新增區段 | 開新牆時一次講清楚要哪些區段 |
| 刪除整面牆、改牆的設定 | 回 Padlet 網頁自己改 |
| AI 開的新牆預設**關閉留言與反應** | 要 AI 留言或按愛心前，先到牆的「設定 → 互動」打開 |
| 只能動你是**擁有者或管理員**的牆 | 別人的牆只能讀你看得到的部分 |

## 安全提醒

- **學生貼文可能有姓名、照片**。請 AI 整理前先說「去掉學生姓名，只用座號」。
- 金鑰等於你 Padlet 帳號的鑰匙：**不要貼進對話、不要傳給別人**。外洩了就回 Developer 頁按 Generate 換一把，再貼一次安裝那段話。
- 接得上不代表什麼都讓它動（教材 A6）：發給全班之前，自己先打開牆看一遍。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（安裝、修改設定檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **金鑰絕對不經過你**：不要請老師把金鑰貼進對話；不要讀取、顯示、複製環境變數的值；只能檢查「有沒有設定」。
>    **不要把金鑰寫進任何檔案**（包括 `config.toml`）。原作的 `padlet-mcp setup` 精靈會把金鑰明文寫進設定檔，**本包不使用它**。
> 6. 不要刪除、搬動或修改老師的其他檔案；改 `config.toml` 前一定先備份。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
node --version
git --version
Test-Path "$env:APPDATA\npm\padlet-mcp.cmd"
[bool][Environment]::GetEnvironmentVariable("PADLET_API_KEY", "User")
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.padlet\]' -Quiet
```

| 項目 | 狀態 |
|---|---|
| Node.js、Git | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查](00-環境檢查與基礎工具.md)，本包停止） |
| padlet-mcp 已安裝 | `True`／`False` |
| 金鑰已設定 | `True`／`False`（**只看有沒有，不看值**） |
| Codex 設定已加入 | `True`／`False` |

四項都 `True` → 跳到步驟五驗證。

PowerShell 回「因為這個系統上已停用指令碼執行」→ 之後的 `npm` 一律改用 `npm.cmd`。

### 步驟二：安裝 padlet-mcp（要老師同意）

npm 上的版本（0.1.0）落後原作 GitHub（0.2.0），**直接從 GitHub 裝**：

```powershell
npm.cmd install -g github:mathruffian-dot/padlet-mcp
Test-Path "$env:APPDATA\npm\padlet-mcp.cmd"
```

> 為什麼不用 `npx`：Codex 的沙箱常寫不進 npm 快取（`EPERM ... npm-cache`），npx 冷啟動也常超過 Codex 預設的 10 秒啟動時限。
> 全域安裝後設定檔寫**完整路徑**最穩。之後要更新，重跑這一行即可。

### 步驟三：請老師設定金鑰（要老師同意；金鑰不經過你）

金鑰已設定（步驟一為 `True`）就跳過。否則建立一個小腳本、另開視窗讓老師自己貼：

```powershell
$helper = Join-Path $env:TEMP "ppsh-set-padlet-key.ps1"
$script = @'
$name = "PADLET_API_KEY"
Write-Host ""
Write-Host "  請貼上 Padlet API key，然後按 Enter" -ForegroundColor Cyan
Write-Host "  （為了安全，畫面上不會顯示你貼的內容）" -ForegroundColor Gray
$s = Read-Host -AsSecureString
$b = [Runtime.InteropServices.Marshal]::SecureStringToBSTR($s)
$v = [Runtime.InteropServices.Marshal]::PtrToStringBSTR($b)
[Runtime.InteropServices.Marshal]::ZeroFreeBSTR($b)
if ($v.Trim().Length -lt 10) {
    Write-Host "  看起來沒有貼到金鑰。請關掉這個視窗，回去跟 AI 說「重來」。" -ForegroundColor Red
} else {
    [Environment]::SetEnvironmentVariable($name, $v.Trim(), "User")
    Write-Host "  已儲存！請關掉這個視窗，回到 AI 說「好了」。" -ForegroundColor Green
}
Read-Host "  按 Enter 關閉"
'@
# 含中文：一定要寫成 UTF-8 with BOM，Windows PowerShell 5.1 才不會亂碼
[IO.File]::WriteAllText($helper, $script, (New-Object Text.UTF8Encoding $true))
Start-Process powershell -ArgumentList "-NoProfile", "-ExecutionPolicy", "Bypass", "-File", "`"$helper`""
```

跟老師說：「我開了一個藍色小視窗，請照『金鑰去哪裡拿』拿到金鑰，貼在小視窗裡按 Enter，完成後跟我說『好了』。」
老師說好了之後，只用這行確認（**不要印出值**），並刪掉小腳本：

```powershell
[bool][Environment]::GetEnvironmentVariable("PADLET_API_KEY", "User")
Remove-Item (Join-Path $env:TEMP "ppsh-set-padlet-key.ps1") -ErrorAction SilentlyContinue
```

### 步驟四：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再把區塊**附加到 `config.toml` 最後面**（已有 `[mcp_servers.padlet]` 就不要重複加，改為檢查內容是否與下面一致）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$cmd = "$env:APPDATA\npm\padlet-mcp.cmd"
$block = @"

# 屏北高中懶人包 #10：Padlet（金鑰放在 Windows 使用者環境變數，這裡不寫金鑰）
[mcp_servers.padlet]
command = '$cmd'
env_vars = ["PADLET_API_KEY"]
startup_timeout_sec = 60
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 路徑用 TOML **單引號字串**，反斜線不用加倍。
- **`env_vars` 一定要寫**：Codex 預設**不會**把電腦上的環境變數傳給 MCP，要明確列出才會轉交。設定檔本身不含金鑰。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面即可。要提醒老師：**之後若重新套用 NMK 連線設定，這段會被蓋掉，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add padlet --scope user -- cmd /c "$env:APPDATA\npm\padlet-mcp.cmd"
```

Claude Code 會把自己的環境變數傳給 MCP，不用另外設定 `env_vars`。

### 步驟五：驗證

**剛改完設定或剛設金鑰**：這個對話還看不到 padlet 工具，Codex 也還沒讀到新的環境變數。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一四項都應為 `True`
2. 呼叫 padlet 的 `whoami` 工具，應回傳老師的帳號名稱
3. 看不到 padlet 工具 → 請老師到 Codex **設定 → MCP servers** 看 `padlet` 是否啟用、有無錯誤訊息
4. `whoami` 回 401／金鑰錯誤 → 請老師回 Developer 頁重新 Generate，回到步驟三重設

### 步驟六：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 10 Padlet（YYYY-MM-DD HH:MM）

- padlet-mcp：已安裝 / 已補裝 / 失敗
- 金鑰：已設定 / 未設定（老師無付費方案）
- Codex 設定：已加入 / 失敗
- whoami：成功（帳號名稱）/ 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟七：回報老師

用白話表格回報，**不要貼指令輸出原文、不要顯示金鑰**：

| 項目 | 結果 |
|---|---|
| Padlet 轉接頭 | ✅／❌ |
| 金鑰 | ✅ 已設定／⚠️ 還沒貼 |
| Codex 設定 | ✅／❌ |
| 連線測試 | ✅ 帳號名稱／⚠️ 要重開後再貼一次／❌ |

最後明確告訴老師下一步，例如：
「請把 Codex **整個關掉再打開**（右下角系統匣也要結束），然後**再貼一次同一段話**，我會幫你做連線測試。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Padlet 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #10` 那一段（先備份）
2. `npm.cmd uninstall -g padlet-mcp`
3. `[Environment]::SetEnvironmentVariable("PADLET_API_KEY", $null, "User")`
4. 提醒老師到 Padlet Developer 頁把舊金鑰作廢

## 來源與查證（2026-09-27）

- padlet-mcp（三師爸 Sense Bar，MIT）：<https://github.com/mathruffian-dot/padlet-mcp>（GitHub v0.2.0；npm 仍是 v0.1.0）
- Padlet API 需付費方案才能產生金鑰：<https://docs.padlet.dev/reference/introduction>
- Codex MCP 設定（`env_vars` 需明確列出、`startup_timeout_sec` 預設 10 秒）：<https://learn.chatgpt.com/docs/extend/mcp>
