# 屏北高中 Agent 基本功懶人包 #11：連接 NotebookLM

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A7 讓教材自己長出來**（一鍵備課包、Gemini × NotebookLM 聯動）
> 使用的轉接頭：[notebooklm-mcp-cli](https://github.com/jacob-bd/notebooklm-mcp-cli)（社群開發，**非 Google 官方**）
> 狀態：🟡 **已依官方與原作資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

裝好之後，你可以直接跟 AI 說：

| 你說 | AI 會做 |
|---|---|
| 「列出我的 NotebookLM 筆記本」 | 列出你帳號裡的筆記本 |
| 「開一本『光合作用備課』筆記本，把這三個網址加進去當資料來源」 | 建筆記本、加來源 |
| 「用這本筆記本產生一份學習指引和 10 題測驗，存到我的資料夾」 | 在 NotebookLM 產生，再下載到你電腦 |

---

## ⚠️ 先知道三件事

1. **這不是 Google 官方工具**。它借用 NotebookLM 網頁的內部介面，Google 改版時可能突然失效，要等作者更新。
2. **登入大約 2–4 週會過期**，過期時再貼一次安裝那段話，AI 會帶你重新登入。
3. **學校帳號（@ppsh.ptc.edu.tw）**：作者只保證一般 Google 帳號有定期測試。學校帳號多半能用，但如果登入後說「無法使用 NotebookLM」，請改用個人 Gmail 帳號，或聯絡學校 Google 管理員。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. **瀏覽器會跳出 Google 登入頁**：用你要給 AI 用的那個 Google 帳號登入（帳號密碼只在瀏覽器輸入，**不要告訴 AI**）
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/11-MCP-NotebookLM.md
照其中「給 AI Agent 的執行步驟」，幫我把 NotebookLM 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
列出我的 NotebookLM 筆記本清單。
```

能列出來（就算是空的）就成功了。再試一次真的動作：

```text
建一本叫「連線測試」的 NotebookLM 筆記本，確認建好了之後再把它刪掉。
```

---

## 已知限制（研習時要講）

| 現象 | 原因 | 怎麼辦 |
|---|---|---|
| 突然說「驗證失敗」「未登入」 | 登入過期（約 2–4 週） | 再貼一次安裝那段話，重新登入 |
| 某個功能昨天可以、今天不行 | Google 改了 NotebookLM 網頁 | 等作者更新；AI 會在重貼安裝那段話時自動更新 |
| 產生影片／音訊很久 | NotebookLM 本身就慢 | 讓它跑，不要一直催 |
| 學校帳號登入後不能用 | 學校管理員未開放或帳號類型不支援 | 改用個人帳號，或問學校 Google 管理員 |

## 安全提醒

- **含學生個資的檔案不要丟進 NotebookLM**（成績、輔導紀錄、名單），先去識別化。
- AI 看得到你這個 Google 帳號裡**所有**筆記本。研習用、教學用最好跟私人筆記分開帳號。
- 登入資料存在你電腦的使用者資料夾裡，**不要把整個使用者資料夾分享或上傳**；要把 AI 跟這個帳號斷開，請 AI 照文末「復原」處理。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（安裝、修改設定檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **Google 登入由老師在瀏覽器完成**：不要詢問、代填或記錄帳號密碼；不要讀取、顯示或複製登入資料夾裡的 cookie 檔。
> 6. 不要刪除、搬動或修改老師的其他檔案；改 `config.toml` 前一定先備份。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過；重複執行時順便更新到最新版。

### 步驟一：檢查（只讀，直接執行）

```powershell
uv --version
$bin = (uv tool dir --bin 2>$null)
Test-Path (Join-Path $bin "nlm.exe")
Test-Path (Join-Path $bin "notebooklm-mcp.exe")
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.notebooklm\]' -Quiet
```

| 項目 | 狀態 |
|---|---|
| uv | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查](00-環境檢查與基礎工具.md)，本包停止） |
| nlm／notebooklm-mcp 已安裝 | `True`／`False` |
| Codex 設定已加入 | `True`／`False` |

已安裝時再檢查登入狀態（只讀）：

```powershell
& (Join-Path $bin "nlm.exe") login --check
```

### 步驟二：安裝或更新（要老師同意）

```powershell
uv tool install notebooklm-mcp-cli      # 未安裝時
uv tool upgrade notebooklm-mcp-cli      # 已安裝時（順便更新，Google 改版後常需要）
```

裝完用步驟一的 `Test-Path` 再確認一次。叫不到 `nlm` 不用管 PATH，**之後一律用 `uv tool dir --bin` 查到的完整路徑執行**。

> 網路上的舊教學寫 `nlm mcp`：這個指令已不存在，MCP 伺服器的執行檔是 `notebooklm-mcp`。

### 步驟三：登入 Google（要老師同意；登入由老師自己做）

`login --check` 已通過就跳過。否則先跟老師說：「等一下會跳出瀏覽器的 Google 登入頁，請用你要給 AI 用的帳號登入，登入完回來跟我說。」然後執行：

```powershell
& (Join-Path (uv tool dir --bin) "nlm.exe") login
```

完成後確認：

```powershell
& (Join-Path (uv tool dir --bin) "nlm.exe") login --check
```

- 沒有自動開瀏覽器、或卡住超過 3 分鐘 → 停下來，請老師截圖給研習講師（**不要改用手動匯入 cookie**，那會經手登入資料）
- 登入成功但說帳號不能用 NotebookLM → 依前面「先知道三件事」第 3 點告訴老師

### 步驟四：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再附加到 `config.toml` 最後面（已有 `[mcp_servers.notebooklm]` 就不要重複加）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$cmd = Join-Path (uv tool dir --bin) "notebooklm-mcp.exe"
$block = @"

# 屏北高中懶人包 #11：NotebookLM（非官方；登入資料存在本機，這裡不含帳密）
[mcp_servers.notebooklm]
command = '$cmd'
startup_timeout_sec = 60
tool_timeout_sec = 180
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 寫**完整路徑**：Codex 啟動 MCP 時不一定吃得到 uv 的 PATH。
- 時限拉長：Codex 預設啟動 10 秒、工具 60 秒；NotebookLM 產生內容常常超過。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面，並提醒老師**之後重新套用 NMK 連線設定會蓋掉這段，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add notebooklm --scope user -- (Join-Path (uv tool dir --bin) "notebooklm-mcp.exe")
```

### 步驟五：建立下載用資料夾（要老師同意）

```powershell
$root = Join-Path ([Environment]::GetFolderPath('MyDocuments')) 'NotebookLM'
'簡報','資訊圖表','音訊','影片','文件','測驗','心智圖' |
    ForEach-Object { New-Item -ItemType Directory -Force -Path (Join-Path $root $_) | Out-Null }
```

之後產出的檔案一律存到這裡（或老師當下的專案資料夾），不要散在桌面。

### 步驟六：驗證

**剛改完設定**：這個對話還看不到 notebooklm 工具。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一全部 `True`、`login --check` 通過
2. 用 notebooklm 工具列出筆記本清單（空的也算成功）
3. 看不到工具 → 請老師到 Codex **設定 → MCP servers** 看 `notebooklm` 是否啟用、有無錯誤訊息
4. 回驗證錯誤 → 回步驟三重新登入

### 步驟七：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 11 NotebookLM（YYYY-MM-DD HH:MM）

- notebooklm-mcp-cli：已安裝（版本 x.x.x）/ 已更新 / 失敗
- Google 登入：成功（帳號類型：個人／學校）/ 失敗
- Codex 設定：已加入 / 失敗
- 列出筆記本：成功 / 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟八：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| NotebookLM 轉接頭 | ✅ 版本／❌ |
| Google 登入 | ✅／❌ |
| Codex 設定 | ✅／❌ |
| 連線測試 | ✅／⚠️ 要重開後再貼一次／❌ |

最後明確告訴老師下一步，並提醒：「**大約每 2–4 週登入會過期**，到時候再貼一次同一段話就好。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 NotebookLM 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #11` 那一段（先備份）
2. `uv tool uninstall notebooklm-mcp-cli`
3. 登入資料：先執行 `nlm login profile list` 看有哪些，**問過老師**再用 `nlm login profile delete <名稱> --confirm` 刪除

## 來源與查證（2026-09-27）

- notebooklm-mcp-cli（jacob-bd，PyPI 0.12.0，2026-09-24 發布）：<https://github.com/jacob-bd/notebooklm-mcp-cli>
- 三師爸 Sense Bar Codex 懶人包 #01（NotebookLM）：<https://github.com/mathruffian-dot/codex-lazy-packs>
- Codex MCP 設定：<https://learn.chatgpt.com/docs/extend/mcp>
