# 屏北高中 Agent 基本功懶人包 #14：連接 GitHub

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A9 不被簡報軟體綁架**（HTML 簡報部署到 GitHub Pages）
> 使用的工具：GitHub CLI（`gh`，00 已安裝）；進階選用 [GitHub 官方 MCP](https://github.com/github/github-mcp-server)
> 狀態：🟡 **已依官方與三師爸資料撰寫，尚未在研習電腦實機測試**

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

讓 AI 替你把做好的網頁、HTML 簡報、互動教材**發布成一個網址**，學生掃 QR Code 就能打開：

| 你說 | AI 會做 |
|---|---|
| 「把這個資料夾的網頁發布上線，給我網址」 | 建 GitHub repo、上傳、開啟 GitHub Pages、回報網址 |
| 「我改好了，幫我更新網站」 | 上傳這次的修改，網址不變 |
| 「幫我做一個這個網址的 QR Code」 | 產生 QR Code 圖檔 |

### 這包用的是「命令列工具」，不是 MCP

GitHub 有三種接法，**發布網頁只需要第一種**：

| 接法 | 做什麼 | 本包 |
|---|---|---|
| **GitHub CLI（`gh`）** | 在你電腦上建 repo、上傳、開 Pages | ✅ 主線 |
| Codex 的 GitHub 外掛 | 在對話裡查 repo、issue | 有就順便登入；**用學校 NMK 點數池的 Codex 可能沒有這個選項，沒關係** |
| GitHub 官方 MCP | 在對話裡查 issue、PR | 進階選用，研習不需要 |

---

## 先準備：GitHub 帳號

還沒有帳號 → 先到 <https://github.com/signup> 用學校信箱註冊（免費）。**帳號名稱會出現在網址裡**（`https://帳號.github.io/…`），取一個你願意讓學生看到的名字。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. **畫面會出現一組 8 碼驗證碼**，瀏覽器會開 GitHub 授權頁：把驗證碼輸進去、按授權（密碼只在瀏覽器輸入，**不要告訴 AI**）
5. AI 可能會問你的**姓名和 email**（用來標示是誰上傳的，會公開在 GitHub 上）

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/14-MCP-GitHub.md
照其中「給 AI Agent 的執行步驟」，幫我把 GitHub 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

跟 AI 說：

```text
幫我確認 GitHub 登入狀態，告訴我帳號名稱。
```

想真的發布一次看看（會在你的 GitHub 建一個**公開**的測試網站）：

```text
幫我建一個叫 github-test 的公開網站，首頁寫「GitHub 連接成功」，開好 GitHub Pages 後給我網址。測完問我要不要刪掉。
```

第一次發布要等 **1–3 分鐘**，打開看到 404 先等一下再重新整理。

---

## 安全提醒（研習時要講）

- **GitHub Pages 的網站是公開的**，任何人拿到網址都看得到，而且會被搜尋引擎找到。**學生名單、成績、照片、金鑰一律不能放上去**。
- repo 就算設成私人，免費帳號的 Pages 網站**仍然是公開的**。
- 發布前先說「列出你要上傳哪些檔案給我看」，確認沒有夾帶不該公開的東西。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦或 GitHub 帳號的步驟**（登入、設定、建 repo、刪 repo）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **GitHub 登入由老師在瀏覽器完成**：不要詢問或代填密碼；不要讀取、顯示 token（`gh auth token` 禁止執行）。
> 6. 不要刪除、搬動或修改老師的其他檔案；**刪除 GitHub repo 一定要老師明確說要刪**。
> 7. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。
> 8. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
git --version
gh --version
gh auth status
git config --global user.name
git config --global user.email
```

| 項目 | 狀態 |
|---|---|
| Git、GitHub CLI | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查](00-環境檢查與基礎工具.md)，本包停止） |
| GitHub 登入 | 已登入（帳號名稱）／未登入 |
| Git 署名 | 已設定／未設定 |

`gh` 回 `Access is denied`（讀不到 `AppData\Roaming\GitHub CLI\config.yml`）：這是 Codex 的權限範圍擋住，不是 gh 壞掉。重新執行並讓老師按同意授權即可（三師爸實測）。

全部都有 → 跳到步驟四。

### 步驟二：登入 GitHub（要老師同意；登入由老師自己做）

先跟老師說：「等一下畫面會出現 8 碼驗證碼，瀏覽器會打開 GitHub，請把驗證碼輸入、按授權，完成後跟我說。」然後執行：

```powershell
gh auth login --hostname github.com --git-protocol https --web
```

- 把輸出裡的**一次性驗證碼**用大字告訴老師（這組碼不是密碼，可以顯示）
- 瀏覽器沒自動開 → 請老師手動打開 <https://github.com/login/device>
- 指令卡住等按 Enter、或這個對話不能互動 → 改開一個獨立視窗讓老師照著畫面做：

```powershell
Start-Process powershell -ArgumentList "-NoExit", "-Command", "gh auth login --hostname github.com --git-protocol https --web"
```

完成後用 `gh auth status` 確認，帳號名稱要是老師的，`Token scopes` 至少有 `repo`。

### 步驟三：設定 Git 署名（要老師同意）

未設定時，問老師要用的姓名與 email，並提醒「這會公開在 GitHub 上；不想公開 email 可以用 GitHub 提供的 noreply 信箱」。
老師不確定時，用 GitHub 的 noreply 信箱最安全：

```powershell
$login = gh api user --jq .login
$id = gh api user --jq .id
git config --global user.name "<老師提供的姓名>"
git config --global user.email "$id+$login@users.noreply.github.com"
```

### 步驟四：Codex 的 GitHub 外掛（只檢查，不改設定檔）

請老師看 Codex **設定 → 外掛程式（Plugins）** 有沒有 GitHub：

- 有 → 請老師按「連接／Connect」，在瀏覽器授權（repo 範圍新手可選「全部」）
- 沒有這個選項 → **正常**（學校 NMK 點數池的 Codex 可能沒有），報告寫「不適用」，不影響發布網頁

**不要**為了這一步去改 `config.toml`。

### 步驟五：驗證（只讀）

```powershell
gh auth status
gh api user --jq .login
```

看得到老師的帳號名稱就完成。**發布測試（會建公開 repo）只在老師要求時做**，流程照「裝好之後：驗收」那段：

```powershell
# 在老師指定或新建的測試資料夾中
git init
git add index.html
git commit -m "GitHub 連線測試頁"
gh repo create github-test --public --source=. --push
$owner = gh api user --jq .login
gh api "repos/$owner/github-test/pages" -X POST -f "source[branch]=main" -f "source[path]=/"
```

Pages 指令失敗多半是 repo 剛建好，等 30 秒再試一次。網址是 `https://<帳號>.github.io/github-test/`。
測完**問老師**要不要刪；老師明確說要刪才執行 `gh repo delete github-test --yes`（需要 `delete_repo` 權限，沒有就請老師到 repo 網頁的 Settings 最下方自己刪）。

### 步驟六（選用，老師明確要求才做）：GitHub 官方 MCP

研習**不需要**。老師要在對話裡查 issue／PR 時才做：

1. 請老師到 <https://github.com/settings/personal-access-tokens> 建一把 **fine-grained token**，只勾需要的 repo 與權限
2. 金鑰**不經過你**：照 [10 Padlet 懶人包](https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/10-MCP-Padlet.md)「步驟三」的小視窗做法，把變數名換成 `GITHUB_PAT_TOKEN`
3. 先備份，再附加到 `config.toml`：

```toml
# 屏北高中懶人包 #14：GitHub 官方遠端 MCP（token 放在 Windows 使用者環境變數）
[mcp_servers.github]
url = "https://api.githubcopilot.com/mcp/"
bearer_token_env_var = "GITHUB_PAT_TOKEN"
```

4. 請老師完全重開 Codex 後再貼一次本段話驗證

**你是 Claude Code**（未實測）：步驟一～三、五相同；Claude Code 沒有 Codex 外掛，步驟四寫「不適用」。

### 步驟七：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 14 GitHub（YYYY-MM-DD HH:MM）

- GitHub CLI 登入：成功（帳號名稱）/ 失敗
- Git 署名：已設定（是否用 noreply 信箱）/ 未設定
- Codex GitHub 外掛：已連接 / 不適用 / 待老師連接
- 發布測試：成功（網址）/ 未做 / 失敗
- 官方 MCP：未安裝 / 已安裝
- 問題紀錄：<沒有就寫「無」>
```

### 步驟八：回報老師

用白話表格回報，**不要貼指令輸出原文、不要顯示 token**：

| 項目 | 結果 |
|---|---|
| GitHub 登入 | ✅ 帳號名稱／❌ |
| 上傳署名 | ✅／⚠️ 未設定 |
| Codex GitHub 外掛 | ✅／不適用 |
| 發布測試 | ✅ 網址／未做 |

最後告訴老師：「之後只要說『把這個資料夾的網頁發布上線』就可以了。**上傳前我會先列出檔案給你確認**。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 GitHub 連接移除」時）

1. `gh auth logout --hostname github.com`
2. 有裝官方 MCP：刪 `config.toml` 的 `# 屏北高中懶人包 #14` 那段（先備份）、清掉環境變數 `GITHUB_PAT_TOKEN`，並請老師到 GitHub 設定把 token 作廢
3. 已建立的 repo 與網站**不要動**，除非老師明確說要刪

## 來源與查證（2026-09-27）

- 三師爸 Sense Bar Codex 懶人包 #02（網頁端登入、Access is denied、Pages 開啟）：<https://github.com/mathruffian-dot/codex-lazy-packs>
- GitHub 官方 MCP 的 Codex 設定（`url`＋`bearer_token_env_var`）：<https://github.com/github/github-mcp-server/blob/main/docs/installation-guides/install-codex.md>
- Codex MCP 設定：<https://learn.chatgpt.com/docs/extend/mcp>
