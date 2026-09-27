# 屏北高中 Agent 基本功懶人包 #15：連接 Canva

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：教材尚未涵蓋（A9 簡報延伸）
> 使用的轉接頭：Canva 官方遠端 MCP（<https://mcp.canva.com/mcp>）
> 狀態：🟡 **已依官方資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

裝好之後，你可以直接跟 AI 說：

| 你說 | AI 會做 |
|---|---|
| 「用 Canva 做一張『校慶運動會』的 A4 海報初稿，給我連結」 | 在你的 Canva 帳號建立一份新設計，給你連結 |
| 「幫我搜尋 Canva 裡跟『畢業典禮』有關的設計」 | 搜尋你 Canva 帳號中的既有設計 |
| 「把這份簡報匯出成 PDF」 | 匯出既有設計為 PDF 等格式 |

---

## ⚠️ 先確認

- 需要一個**能登入的 Canva 帳號**（免費版、教育版、付費版都可以連上）。
- **調整既有設計尺寸（resize）需要 Canva Pro 以上方案**；**自動填入、品牌範本、品牌工具組限 Canva Enterprise**。教育版教師帳號通常已是免費升級，其餘功能一般夠用。
- 這包**不用裝任何程式、不用金鑰**：是 Canva 官方提供的遠端連線服務，登入用瀏覽器跳出的 Canva 登入畫面完成，跟平常登入 Canva 網站一樣。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 會請你在**瀏覽器跳出的視窗**登入 Canva 並按「允許」——這一步就跟平常登入 Canva 網站一樣，**不會有金鑰要貼**
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/15-MCP-Canva.md
照其中「給 AI Agent 的執行步驟」，幫我把 Canva 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意或登入的地方跳出來就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

完全重開 Codex（含系統匣圖示）、再貼一次上面那段話之後，跟它說：

```text
用 canva 列出我最近的設計。
```

看到你 Canva 帳號裡的設計清單就成功了。再試一次真的動作：

```text
用 Canva 做一張『校慶運動會』的 A4 海報初稿，給我連結。
```

---

## 已知限制

| 做不到 / 要注意 | 怎麼辦 |
|---|---|
| 調整既有設計尺寸（resize） | 需要 Canva Pro 以上方案 |
| 自動填入、品牌範本、品牌工具組 | 限 Canva Enterprise |
| 只能動你自己 Canva 帳號裡、你有權限的設計 | 別人的設計要先分享給你 |
| Codex 是否支援 Canva MCP，本文件**尚未實機驗證** | 卡住就截圖給研習講師 |

## 安全提醒

- **學生照片或姓名要放進設計前，先確認已取得使用同意。**
- AI 產出的設計**發布或印出前自己看過一遍**，不要沒看內容就直接發給全班或家長。
- 通道和權限是兩件事：接得上不代表什麼都讓它動（教材 A6）。
- 覺得授權有問題（例如換了電腦、離職）：到 Canva 帳號設定裡撤銷這個連線的授權即可，不用改任何檔案。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（修改設定檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **這包沒有金鑰**：登入一律走瀏覽器跳出的 Canva 官方登入畫面，不要幫老師輸入帳密，也不要要求老師把任何金鑰或密碼貼進對話。
> 6. 不要刪除、搬動或修改老師的其他檔案；改 `config.toml` 前一定先備份。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.canva\]' -Quiet
```

`True` → Codex 設定已加入，跳到步驟三登入；`False` → 進行步驟二。

### 步驟二：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再把區塊**附加到 `config.toml` 最後面**（已有 `[mcp_servers.canva]` 就不要重複加）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$block = @"

# 屏北高中懶人包 #15：Canva（官方遠端 MCP，OAuth 登入，不含金鑰）
[mcp_servers.canva]
url = "https://mcp.canva.com/mcp"
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 這是**遠端** MCP，設定檔裡沒有本機路徑、沒有金鑰。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面即可。要提醒老師：**之後若重新套用 NMK 連線設定，這段會被蓋掉，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add --transport http canva https://mcp.canva.com/mcp --scope user
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
& $codex mcp login canva
```

這會開啟瀏覽器，請老師登入 Canva 帳號並按「允許」。

若找不到執行檔或登入失敗（**此步驟未實測，可能因版本而異**）：請老師到 Codex **設定 → MCP servers** 找到 `canva`，按登入／Authenticate。

### 步驟四：驗證

**剛加設定或剛登入**：這個對話還看不到 canva 工具。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一應為 `True`
2. 呼叫 canva 工具列出最近的設計，應能回傳清單
3. 看不到 canva 工具 → 請老師到 Codex **設定 → MCP servers** 看 `canva` 是否啟用、有無錯誤訊息
4. 登入失敗或被拒 → 回到步驟三重新登入一次

### 步驟五：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 15 Canva（YYYY-MM-DD HH:MM）

- Codex 設定：已加入 / 失敗
- 登入：成功（Canva 帳號）/ 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟六：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| Canva 轉接頭 | ✅／❌ |
| 登入 | ✅ 已登入／⚠️ 要重開後再貼一次／❌ |
| 連線測試 | ✅ 看得到設計清單／⚠️ 待驗證／❌ |

最後明確告訴老師下一步，例如：
「請把 Codex **整個關掉再打開**（右下角系統匣也要結束），然後**再貼一次同一段話**，我會幫你做連線測試。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Canva 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #15` 那一段（先備份）
2. 提醒老師到 Canva 帳號設定（Apps and integrations／已連結的應用程式）撤銷這個連線的授權

## 來源與查證（2026-09-27）

- Canva 官方遠端 MCP 說明：<https://www.canva.dev/docs/apps/mcp/>
- Canva 官方新聞稿（MCP Server 上線）：<https://www.canva.com/newsroom/news/deep-research-integration-mcp-server/>
- 第三方 MCP 目錄收錄條目（功能與方案限制對照）：<https://mcpservers.org/remote-mcp-servers/canva>
