# 屏北高中 Agent 基本功懶人包 #16：連接 Kahoot

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：教材尚未涵蓋（概念入門版的聽講段評量）
> 使用的轉接頭：Kahoot 官方遠端 MCP（<https://mcp.kahoot.it/mcp>）
> 狀態：🟡 **已依官方資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

裝好之後，你可以直接跟 AI 說：

| 你說 | AI 會做 |
|---|---|
| 「幫我用這份教材的重點，做一個 5 題的 Kahoot 概念辨識測驗」 | 在你的 Kahoot 帳號建立一個新的 kahoot，題目是選擇題或是非題 |
| 「把第 3 題的選項改一下」 | 編輯既有 kahoot 的題目 |
| 「列出我最近建立的 kahoot」 | 列出你帳號裡的 kahoot 清單 |

---

## ⚠️ 先確認

- 需要一個**能登入的 Kahoot 帳號**。
- **目前只支援傳統的選擇題與是非題**，比較進階的題型（例如拼圖、投票）之後才會支援。
- 這包**不用裝任何程式、不用金鑰**：是 Kahoot 官方提供的遠端連線服務，登入用瀏覽器跳出的 Kahoot 登入畫面完成，跟平常登入 Kahoot 網站一樣。
- Kahoot 官方說明頁提到可搭配 ChatGPT、Claude 等 AI 助理使用；**是否支援 Codex、需要哪種 Kahoot 方案，目前無法從官方頁面確認**，若登入或使用時被拒絕，請截圖回報研習講師。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 會請你在**瀏覽器跳出的視窗**登入 Kahoot 並按「允許」——這一步就跟平常登入 Kahoot 網站一樣，**不會有金鑰要貼**
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/16-MCP-Kahoot.md
照其中「給 AI Agent 的執行步驟」，幫我把 Kahoot 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意或登入的地方跳出來就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

完全重開 Codex（含系統匣圖示）、再貼一次上面那段話之後，跟它說：

```text
用 kahoot 列出我的 kahoot。
```

看到你 Kahoot 帳號裡的清單就成功了。再試一次真的動作：

```text
幫我做一個 3 題的 Kahoot，內容是「AI 是不是萬能的」概念辨識題（不是診斷題），都用選擇題。
```

---

## 已知限制

| 做不到 / 要注意 | 怎麼辦 |
|---|---|
| 只支援選擇題、是非題 | 進階題型等 Kahoot 之後支援 |
| **Kahoot 有速度分，會獎勵猜測，診斷性題目不要放 Kahoot**（教材已定案） | 診斷題留在 Google 表單，Kahoot 只放**課中概念辨識題** |
| Codex 是否支援、需要哪種方案，**官方頁面未能讀取確認** | 登入被拒就截圖回報研習講師 |
| MCP 一時用不了 | 備案：AI 直接產生題目文字，老師到 Kahoot 建立頁用「匯入試算表」功能貼上（此功能是否需要付費方案，以 Kahoot 畫面顯示為準） |

## 安全提醒

- **學生暱稱不要用真名**，遊玩時投影出來全班看得到。
- 通道和權限是兩件事：接得上不代表什麼都讓它動（教材 A6）。
- 覺得授權有問題（例如換了電腦、離職）：到 Kahoot 帳號設定裡撤銷這個連線的授權即可，不用改任何檔案。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（修改設定檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **這包沒有金鑰**：登入一律走瀏覽器跳出的 Kahoot 官方登入畫面，不要幫老師輸入帳密，也不要要求老師把任何金鑰或密碼貼進對話。
> 6. 不要刪除、搬動或修改老師的其他檔案；改 `config.toml` 前一定先備份。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.kahoot\]' -Quiet
```

`True` → Codex 設定已加入，跳到步驟三登入；`False` → 進行步驟二。

### 步驟二：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再把區塊**附加到 `config.toml` 最後面**（已有 `[mcp_servers.kahoot]` 就不要重複加）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$block = @"

# 屏北高中懶人包 #16：Kahoot（官方遠端 MCP，OAuth 登入，不含金鑰）
[mcp_servers.kahoot]
url = "https://mcp.kahoot.it/mcp"
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 這是**遠端** MCP，設定檔裡沒有本機路徑、沒有金鑰。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面即可。要提醒老師：**之後若重新套用 NMK 連線設定，這段會被蓋掉，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add --transport http kahoot https://mcp.kahoot.it/mcp --scope user
```

之後在 Claude Code 對話輸入 `/mcp` 進行登入。

### 步驟三：登入（老師在瀏覽器做）

先找 Codex 執行檔：

```powershell
$codex = (Get-Command codex -ErrorAction SilentlyContinue).Source
if (-not $codex) {
    $codex = Get-ChildItem "$env:LOCALAPPDATA\OpenAI\Codex\bin\*\codex.exe" -ErrorAction SilentlyContinue |
        Sort-Object LastWriteTime -Descending | Select-Object -First 1 -ExpandProperty FullName
}
```

找到就執行：

```powershell
& $codex mcp login kahoot
```

這會開啟瀏覽器，請老師登入 Kahoot 帳號並按「允許」。

若找不到執行檔或登入失敗（**此步驟未實測，可能因版本而異，也可能因 Codex 不在官方支援清單而被拒**）：請老師到 Codex **設定 → MCP servers** 找到 `kahoot`，按登入／Authenticate；若明確被拒絕，請截圖回報研習講師。

### 步驟四：驗證

**剛加設定或剛登入**：這個對話還看不到 kahoot 工具。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一應為 `True`
2. 呼叫 kahoot 工具列出我的 kahoot，應能回傳清單
3. 看不到 kahoot 工具 → 請老師到 Codex **設定 → MCP servers** 看 `kahoot` 是否啟用、有無錯誤訊息
4. 登入失敗或被拒 → 回到步驟三重新登入一次；若確定是 Codex 不支援，改用「已知限制」裡的匯入試算表備案

### 步驟五：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 16 Kahoot（YYYY-MM-DD HH:MM）

- Codex 設定：已加入 / 失敗
- 登入：成功（Kahoot 帳號）/ 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟六：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| Kahoot 轉接頭 | ✅／❌ |
| 登入 | ✅ 已登入／⚠️ 要重開後再貼一次／❌ |
| 連線測試 | ✅ 看得到 kahoot 清單／⚠️ 待驗證／❌ |

最後明確告訴老師下一步，例如：
「請把 Codex **整個關掉再打開**（右下角系統匣也要結束），然後**再貼一次同一段話**，我會幫你做連線測試。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Kahoot 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #16` 那一段（先備份）
2. 提醒老師到 Kahoot 帳號設定（已連結的應用程式）撤銷這個連線的授權

## 來源與查證（2026-09-27）

- Kahoot 官方說明：如何用 MCP Server 連接 ChatGPT、Claude 等 AI 助理：<https://support.kahoot.com/hc/en-us/articles/36770398743581-How-to-connect-ChatGPT-Claude-and-other-AI-Assistants-to-Kahoot-using-the-MCP-Server>
