# 屏北高中 Agent 基本功懶人包 #13：連接 Wordwall（命令列技能，不是 MCP）

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A8 一份教材生出 30 種遊戲**
> 使用的工具：[wordwall-cli](https://github.com/mathruffian-dot/wordwall-cli)（三師爸 Sense Bar 開發，MIT 授權）
> 狀態：🟡 **已依原作資料撰寫，尚未在研習電腦實機測試**

Wordwall 沒有公開 API，也沒有官方 MCP，只能靠瀏覽器自動化操作。三師爸 Sense Bar 把這套自動化寫成一支
命令列工具（`wordwall.py`，底層用 Playwright 幫你在瀏覽器裡按按鈕），再包一頁說明書（`SKILL.md`）讓 AI
知道什麼時候、怎麼用它。這就是教材四階降級「內建連接器 → MCP → CLI → 瀏覽器自動化」裡的 **CLI 這一階**：
沒有更省事的連法，但比讓 AI 自己亂點瀏覽器可靠、可重複。

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

讓 AI 直接在 Wordwall 上幫你建立互動遊戲、發作業、抓成績：

| 你說 | AI 會做 |
|---|---|
| 「用 Wordwall 幫我把這 5 題因數倍數題做成 Quiz，先給我看題目，我確認後再建立」 | 規劃範本、產生內容、**先給你看過**，你說可以才正式建立 |
| 「把剛剛那個活動指派給 302 班，設成 9/30 截止」 | 設定學生作業，回傳學生要點的連結 |
| 「幫我看一下 302 班那個活動的作答成績」 | 讀取成績清單（只看作答人數，不主動顯示學生姓名），需要下載時匯出 Excel／CSV |

**AI 不會沒問過你就送出。** 原作把流程固定成「規劃 → 先做一次不送出的預覽 → 你確認 → 才正式建立」，
這是工具本身的設計，不是老師要自己記得盯著。

### 目前能建立的遊戲

Quiz、配對（Match up／Find the match／Flash cards）、分類（Group sort／Speed sorting）、
簡易轉盤與卡片（Speaking cards、Spin the wheel 簡易模式）、句子填空（Complete the sentence）、
是非題（True or false）、開箱（Open the box 簡易模式）、排序（Rank order）、標示圖（Labelled diagram）。
其餘範本（Crossword、問答轉盤等）原作仍在實測中，AI 若判斷需要用到，會直接說明目前做不到，
**不會偷偷換成別的範本交差**。

### 如果只是要「教材變互動小遊戲」，不一定要用這包

如果你不特別在意一定要用 Wordwall 的介面（例如要用它的轉盤、配對牌、累積成績等特有功能），
其實直接請 AI 做一個網頁小遊戲、匯出成一個 HTML 檔給學生玩更快，不用登入、也不會被 Wordwall 改版影響。
**只有你需要 Wordwall 特有的範本、內建成績追蹤、或社群題庫時**，才需要裝這包。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 說「請你去登入 Wordwall」時，會跳出一個**專用的 Chrome 視窗**，你用自己的 Wordwall 帳號（Google
   或 Email 皆可）登入，登入完回去跟 AI 說一聲「登入好了」就好
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/13-MCP-Wordwall.md
照其中「給 AI Agent 的執行步驟」，幫我把 Wordwall 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
需要我登入 Wordwall 帳號時，請你開瀏覽器讓我自己輸入帳號密碼，不要問我密碼是什麼。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**還沒有 Wordwall 帳號？** 到 [wordwall.net](https://wordwall.net) 用學校信箱申請一個免費的老師帳號即可，
申請這一步請老師自己做，AI 不會、也不該幫你申請帳號或記你的密碼。

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
用 wordwall-cli 幫我出一個 3 題的選擇題 Quiz 測試用，內容隨便，先做 dry-run 給我看，不要真的建立。
```

看得到題目預覽、且沒有出現錯誤，代表連線正常。確認沒問題後，這個測試內容不用理它，本來就不會真的送到 Wordwall。

---

## 安全提醒

- **AI 不會、也看不到你的 Wordwall 帳號密碼**：登入一律是你自己在跳出的 Chrome 視窗裡輸入，AI 只是幫你把那個
  視窗打開。任何時候如果 AI 反過來問你「密碼是什麼」，都不要回答，直接跟研習講師反映。
- **成績資料是學生個資**：下載成績時，學生欄位請用**班級座號**而非真實姓名；成績檔（Excel／CSV）**只留在自己電腦，不要放進 GitHub**。
- **建立與發佈前先看過內容**：AI 會先做一次不送出的預覽（`dry-run`）讓你看題目、答案對不對，你說「可以」才會正式建立、發佈或指派作業。**送出去、發布出去的東西是收不回來的**，看一眼再確認（教材 A6）。
- **Wordwall 免費帳號可建立的活動數量有上限**，實際數字以 Wordwall 官網說明為準；快用完時 AI 會如實回報，不會自作主張刪掉你的舊活動。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（clone、安裝套件、下載 Chromium）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **絕不可向老師索取、代填或記錄 Wordwall 帳號密碼**。登入一律是 `chrome-login` 開出真實 Chrome 讓老師本人輸入，你只執行 `chrome-login` 與 `grab-session` 這兩個指令，不碰帳密本身。
> 6. **不要用 Codex 內建的 `$skill-installer`**，也不要把工具放進 `.codex\skills`；一律 clone 到 `~/.agents/skills/wordwall-cli`（Codex 官方個人技能資料夾）。
> 7. 建立、指派、下載成績這類會送出資料或留下紀錄的動作，**固定順序**：`plan` → `--dry-run` → `--editor-check`（如適用）→ 老師確認 → 才移除 `--dry-run` 正式執行。**不可跳過確認直接送出**。
> 8. 遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**（例如不要改用其他未經查證的 Wordwall 自動化工具）。
> 9. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

先判斷 Python 叫法（沿用 [00 環境檢查](00-環境檢查與基礎工具.md) 的規則）：

```powershell
git --version
python --version
py -0p
```

- `python --version` 有版本號 → 之後都用 `python`。
- `python --version` 跳出 Microsoft Store、沒反應、或找不到 → 看 `py -0p`：**有列出版本**（例如 `-V:3.13`）就改用
  `py -3.13`（換成列出的版本），**之後所有指令都用這個叫法**，並記進環境檢查報告。
- 兩者都沒有 → 請老師先做 [00 環境檢查與基礎工具](00-環境檢查與基礎工具.md)，本包停止。

再檢查 Chrome 與技能是否已安裝：

```powershell
Test-Path "C:\Program Files\Google\Chrome\Application\chrome.exe"
Test-Path "$env:USERPROFILE\.agents\skills\wordwall-cli\SKILL.md"
Test-Path "$env:USERPROFILE\.claude\skills\wordwall-cli\SKILL.md"
```

| 項目 | 狀態 |
|---|---|
| Git | 有版本號才算有（沒有 → 請老師先做 00，本包停止） |
| Python | 版本號＋叫法（`python` 或 `py -3.xx`）（沒有 → 請老師先做 00，本包停止） |
| Google Chrome | `True`／`False`（wordwall-cli 的登入功能需要**真正的 Google Chrome**，不能用 Edge 代替；沒有的話下一步先問老師要不要安裝） |
| Codex 技能已存在 | `True`／`False`（你是 Codex 時看這行） |
| Claude Code 技能已存在 | `True`／`False`（你是 Claude Code 時看這行） |

技能已存在 → 跳到步驟三驗證環境；沒有 Chrome 且老師同意安裝 → 執行
`winget install --id Google.Chrome -e --accept-source-agreements --accept-package-agreements`。

### 步驟二：取得工具並安裝環境（要老師同意）

**你是 Codex**：clone 進 Codex 的個人技能資料夾（Codex 會自動讀取其中的 `SKILL.md`）：

```powershell
$skillPath = "$env:USERPROFILE\.agents\skills\wordwall-cli"
if (Test-Path $skillPath) {
    git -C $skillPath pull
} else {
    git clone https://github.com/mathruffian-dot/wordwall-cli.git $skillPath
}
```

**你是 Claude Code**：改放 `$env:USERPROFILE\.claude\skills\wordwall-cli`，其餘步驟相同（把下面的
`$skillPath` 換成這個路徑）。

> 不要用 Codex 內建的 `$skill-installer`，它會裝到 `~/.codex/skills`，官方個人技能資料夾其實是
> `~/.agents/skills`（Codex 也會讀）。

**不要直接執行 repo 內的 `setup.ps1`**——它寫死呼叫 `python`，遇到市集空殼 Python 會失敗。改由你用
步驟一判定好的 Python 叫法，照 `setup.ps1` 的內容逐步執行（把 `<python>` 換成 `python` 或 `py -3.xx`）：

```powershell
<python> -m pip install -r "$skillPath\requirements.txt"
<python> -m playwright install chromium
```

`playwright install chromium` 會下載約 170MB 的瀏覽器核心，**先跟老師說要等一下**，不要讓他以為當機了。

PDF 截圖功能是選用的，只有老師明確說要用 PDF 出題時才裝：

```powershell
<python> -m pip install -r "$skillPath\requirements-pdf.txt"
```

安裝完先跑一次診斷（只讀）：

```powershell
<python> "$skillPath\wordwall.py" doctor --pdf
```

`doctor` 若回報缺少元件，會直接列出安裝指令，照上面的方式補裝後再跑一次，直到通過為止。

### 步驟三：登入 Wordwall（老師本人做）

跟老師說：「接下來會跳出一個專用的 Chrome 視窗，請你用自己的 Wordwall 帳號登入，登入完回來跟我說一聲」，然後執行：

```powershell
<python> "$skillPath\wordwall.py" chrome-login
```

- 這會開一個**專用**的 Chrome（用自己的 profile 與埠 `9333`，不會連到老師平常用的 Chrome，也不會碰
  NotebookLM 等其他工具的登入狀態）。
- 若顯示埠被占用，改用 `chrome-login --port 9334`。
- **絕不索取、代填或記錄老師的帳號密碼**，全程由老師自己在跳出的視窗操作。

老師說登入好了之後：

```powershell
<python> "$skillPath\wordwall.py" grab-session
<python> "$skillPath\wordwall.py" check
```

看到 `[OK] 登入有效` 就完成。登入狀態存在老師電腦的 `~/.wordwall/state.json`，**這個檔案不可上傳、
不可放進 GitHub、也不可複製給別的老師**——每人要在自己電腦各自登入一次。

### 步驟四：驗證

```powershell
<python> "$skillPath\wordwall.py" doctor --login --pdf
```

全部通過才算完成。**技能要重新開啟 Codex（或 Claude Code）才會被讀取到**：請老師把 Agent 整個關掉
（含系統匣圖示）再打開，並**再貼一次同一段安裝話術**做最終確認——這次應該會直接看到步驟一三項檢查
都通過，不用重跑安裝。

重開後可請老師做一次「裝好之後：驗收」的 `dry-run` 測試，確認 AI 真的能透過 `wordwall.py` 動作。

### 步驟五：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 13 Wordwall（YYYY-MM-DD HH:MM）

- Python 叫法：python / py -3.xx
- Google Chrome：已安裝 / 已補裝 / 未安裝
- wordwall-cli 位置：~/.agents/skills/wordwall-cli（Codex）/ ~/.claude/skills/wordwall-cli（Claude Code）
- doctor --pdf（環境）：通過 / 失敗
- 登入狀態：已登入 / 待老師登入 / 失敗
- doctor --login --pdf（完整診斷）：通過 / 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟六：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| wordwall-cli 工具 | ✅／❌ |
| Chrome 環境 | ✅／❌ |
| Wordwall 登入 | ✅／⚠️ 待老師登入／❌ |
| 完整診斷 doctor | ✅／⚠️ 要重開後再貼一次／❌ |

全部 ✅ 時，提醒老師：「之後要用 Wordwall 建活動，AI 會先給你看題目預覽，你說可以才會正式建立，成績下載請只用班級座號、成績檔不要放進 GitHub。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Wordwall 連接移除」時）

**先問老師一次再動作**：

1. 刪除技能資料夾：`~/.agents/skills/wordwall-cli`（Codex）或 `~/.claude/skills/wordwall-cli`（Claude Code）
2. 刪除登入狀態：`~/.wordwall`（含 `state.json`）
3. Wordwall 網站上的帳號與已建立的活動**完全不要動**，那是老師自己在 Wordwall 網站上的資料

---

## 已知限制

| 限制 | 說明 |
|---|---|
| 部分範本待實測 | Crossword、問答轉盤／問答盒、標示圖等範本原作仍在實測中，AI 若判斷需要用到會如實告知做不到，不會偷偷換範本 |
| Wordwall 改版可能失效 | 工具靠自動化操作 Wordwall 的網頁介面，Wordwall 改版可能讓選擇器失效，需等原作更新後才會恢復正常 |
| 執行速度較慢 | 瀏覽器自動化本來就比呼叫 API 慢，建立一個活動可能要等幾十秒到一兩分鐘 |
| 尚未實機測試 | 本包依原作 repo 的說明文件撰寫，**尚未在屏北高中研習電腦實際跑過一次完整安裝**，欄位若與畫面不同以實際畫面為準 |

## 來源與查證（2026-09-27）

- wordwall-cli（三師爸 Sense Bar 開發，MIT 授權）：<https://github.com/mathruffian-dot/wordwall-cli>（`INSTALL.md`、`README.md`、`SKILL.md`、`setup.ps1`）
- Codex 官方個人技能資料夾為 `~/.agents/skills`（見本專案 AGENTS.md 注意事項；`$skill-installer` 裝到 `~/.codex/skills` 官方文件未列出）
- Wordwall 官網（帳號申請、免費方案活動數上限）：<https://wordwall.net>
