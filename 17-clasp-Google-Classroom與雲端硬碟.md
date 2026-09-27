# 屏北高中 Agent 基本功懶人包 #17：連接 Google Classroom 與雲端硬碟（clasp，不是 MCP）

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**P2-07 派收批改作業**（L8 教師任務）；L6-2「Google 服務特別麻煩」
> 使用的工具：clasp-setup 技能（三師爸 Sense Bar，[clasp-gas-skill](https://github.com/mathruffian-dot/clasp-gas-skill)，MIT 授權）＋ [classroom-tools](https://github.com/mathruffian-dot/classroom-tools)（Apps Script 範例程式，三師爸 Sense Bar）
> 狀態：🟡 **已依原作資料撰寫，尚未在研習電腦實機測試**

Google Classroom 沒有給一般使用者的公開 API 金鑰、也沒有官方 MCP，官方作法是用 **clasp**（Google 官方的命令列工具）把一段小程式（Apps Script）推上 Google 雲端執行，程式再去呼叫 Classroom。這是教材四階降級「內建連接器 → MCP → CLI → 瀏覽器自動化」裡的 **CLI 這一階**：AI 能真的讀寫，但因為 Google 的安全設計，**貼公告、建作業這種對全班發布的動作，最後一按「執行」一定是老師本人在網頁上按**，AI 沒辦法也不該幫你代按。

**Google 雲端硬碟不一定要裝這包**：如果你的電腦已經裝了「Google 雲端硬碟」桌面版，AI 本來就能直接讀寫那個同步資料夾裡的檔案，完全不需要 clasp。只有要「搜尋整個雲端硬碟」「用程式建立 Google 文件／試算表」「改分享權限」這類進階操作才用得到 Apps Script，而這部分原作 repo 目前沒有現成程式碼，**本包不含**（見文末已知限制）。

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包會幫你做什麼

| 你說 | AI 會做 |
|---|---|
| 「幫我列出我現在教的 Google Classroom 課程」 | 把程式推上雲端，請你到 Apps Script 編輯器選 `listCourses` 按執行，再把「執行記錄」裡的課程與 id 念給 AI 聽 |
| 「幫 302 班貼一則公告：明天期中考範圍到第三章」 | 把公告文字寫進程式、推上去，**請你自己在編輯器按執行**送出（送出前你會先看過文字內容） |
| 「幫我建一份作業：小論文初稿，說明是……」 | 把作業標題與說明寫進程式、推上去，請你按執行建立 |
| 「幫我看 302 班的作業繳交狀況」 | 推上去後請你按執行，執行完會產生一份**新的 Google 試算表**，AI 幫你打開，內容只列座號／姓名與繳交狀態 |
| 「我電腦有裝雲端硬碟，幫我把這份成績單存進去」 | 直接讀寫本機同步資料夾裡的檔案，**完全不需要這包的安裝** |

**AI 不會沒問過你就送出。** 貼公告、建作業、匯出繳交狀況這些會影響全班或看到學生資料的動作，最後一步「按執行」本來就只能由你自己在 Apps Script 編輯器裡按——這正好就是最後的把關動作，不是老師要自己記得多做一步。

### 目前能做的事

- **Classroom**：列出課程、列出某課程學生名單、貼公告、建立作業、列出某課程的作業清單、把整門課的繳交狀況匯出成新的 Google 試算表。
- **雲端硬碟**：桌面同步資料夾裡的檔案讀寫（不需要安裝這包，AI 本來就會）。

其餘操作（修改或刪除已建立的作業、搜尋整個雲端硬碟、用程式建立或分享 Google 文件／試算表）原作 repo 沒有現成程式碼，**本包不含**，AI 不會自己編一段來湊。

### 如果只是要存取雲端硬碟的檔案，不需要裝這包

只要你電腦上已經裝了「Google 雲端硬碟」桌面版，AI 就能直接讀、寫、整理那個同步資料夾裡的檔案，跟平常請 AI 處理你電腦上的檔案一樣，**不用 clasp、不用登入、不用這包**。這包只在你要動 **Google Classroom** 時才需要。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 說「請你打開 Apps Script API 開關」時，用你**任教的學校帳號**（`@ppsh.ptc.edu.tw`）登入那個網頁把開關打開，等 1～2 分鐘再回去跟 AI 說一聲
5. AI 說「請你登入」時，會跳出瀏覽器，請用**同一個學校帳號**登入 Google 並按允許（因為你的課程就開在這個帳號底下，不能用個人 Gmail）
6. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/17-clasp-Google-Classroom與雲端硬碟.md
照其中「給 AI Agent 的執行步驟」，幫我把 Google Classroom 的 clasp 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
需要我登入 Google 帳號或打開某個設定開關時，請你講清楚要我做什麼、打開瀏覽器讓我自己操作，不要問我密碼是什麼。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**這包的前提是你已經在用 Google Classroom 授課。** 如果你目前沒有開課程，這包對你暫時沒有用處。

**若登入後出現「被系統管理員封鎖」或 Apps Script／Classroom 相關功能無法使用**：這是學校 Google 網域的管理設定，你自己解不了，請聯絡學校 Google 系統管理員（秘書）協助開通。

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
用 clasp 幫我把 Classroom 工具的程式推上去，推完告訴我要去哪裡按執行。
```

AI 應該會清楚告訴你「去 Apps Script 編輯器、選 `listCourses`、按執行」。你按下去、看到「執行記錄」列出你的課程清單，就代表連線正常。把裡面的課程名稱與 id 念給 AI 聽（或截圖），AI 之後就能針對這門課幫你操作。

---

## 安全提醒

- **學生姓名與 email 是個資**：只有在你明確要求時，AI 才會列出學生名單或繳交狀況；能用班級座號就優先用座號。名單與成績請存成檔案留在自己電腦，**不要整份貼進對話裡，也不要放進任何會同步到 GitHub 的地方**。
- **貼公告、建作業前一定先看過內容**：這些動作最後一步是你自己在 Apps Script 編輯器裡按「執行」——**送出去、對全班發布的東西是收不回來的**，按之前務必再看一眼（教材 A6）。
- **AI 不會、也看不到你的 Google 帳號密碼**：登入一律是你自己在跳出的瀏覽器裡輸入。任何時候如果 AI 反過來問你密碼，不要回答，直接跟研習講師反映。
- **登入狀態不可外流**：clasp 的登入憑證存在你電腦裡（`.clasprc.json`），AI 不可讀出內容、不可上傳、也不可放進 GitHub。
- **學校帳號被管理員擋下時，找秘書（Google 系統管理員）處理**，不要自己在 Google 後台亂試各種設定。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**（clasp、clasp-setup 技能、classroom-tools 專案），不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦的步驟**（安裝、clone、建立 Apps Script 專案）：照你所在 Agent 的權限確認機制取得老師同意。**只讀不改的檢查指令**可以直接執行。
> 4. `clasp login` **一律用老師任教的學校帳號**（`@ppsh.ptc.edu.tw`），**不要**照 clasp-setup 一般規則建議用個人 Gmail——因為 Classroom 課程開在學校帳號底下，換帳號會看不到課程。
> 5. 若登入回 `admin_policy_enforced`：**不要重試硬解**，直接停下來，請老師聯絡學校 Google 系統管理員（秘書）確認 Apps Script API／Classroom API 已開放、OAuth Client 未被擋。
> 6. **絕不可向老師索取、代填或記錄帳號密碼**，也不可讀出、上傳或以任何方式外流 `.clasprc.json` 的內容。
> 7. **不要用 Codex 內建的 `$skill-installer`**，也不要把技能放進 `.codex\skills`；一律放進 `~/.agents/skills`（Codex 官方個人技能資料夾）。
> 8. Apps Script 專案放在老師指定或新建的資料夾，**不要放進任何會推上 GitHub 的專案資料夾**。
> 9. 學生姓名／email 是個資：**只在老師明確要求時才列出**，優先用座號；名單與成績存成檔案放老師電腦，不要整份貼進對話。
> 10. **貼公告、建作業、匯出繳交狀況**：你只負責把內容準備好、`clasp push` 上去，**最後按「執行」一定要老師自己在 Apps Script 編輯器點**——不要嘗試用 clasp CLI 代為觸發執行（目前也做不到）。
> 11. 遇到錯誤先停下來用白話說明，**不要換成本文件以外未經查證的方法硬裝**。
> 12. 可以重複執行：已完成的項目檢查通過就跳過。

### 步驟一：檢查（只讀，直接執行）

```powershell
node --version
git --version
Get-Command clasp -ErrorAction SilentlyContinue
Test-Path "$env:USERPROFILE\.agents\skills\clasp-setup\SKILL.md"
Test-Path "$env:USERPROFILE\.claude\skills\clasp-setup\SKILL.md"
```

| 項目 | 狀態 |
|---|---|
| Git | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查與基礎工具](00-環境檢查與基礎工具.md)，本包停止） |
| Node.js | clasp v3 要求 **20 以上**；沒有或版本太舊 → 問老師要不要安裝 Node.js LTS（比照 00 的做法） |
| clasp | 有版本號才算已裝，沒有就進步驟二安裝 |
| Codex 技能已存在 | `True`／`False`（你是 Codex 時看這行） |
| Claude Code 技能已存在 | `True`／`False`（你是 Claude Code 時看這行） |

技能與 clasp 都已存在 → 跳到步驟三確認登入狀態。

### 步驟二：安裝 clasp 與 clasp-setup 技能（要老師同意）

安裝 clasp 本身，用 `npm.cmd install`，**不要用 `npx`**（Codex 沙箱寫不進 npm 快取，且本包要老師之後能重複用）：

```powershell
npm.cmd install -g @google/clasp
clasp --version
```

`clasp --version` 沒反應 → 檢查是否需要重開一次終端機或 Codex 再試一次。

技能複製到 Codex 的個人技能資料夾（Claude Code 改放 `$env:USERPROFILE\.claude\skills`，其餘相同）：

```powershell
git clone https://github.com/mathruffian-dot/clasp-gas-skill.git "$env:TEMP\clasp-gas-skill"
Copy-Item -Recurse -Force "$env:TEMP\clasp-gas-skill\skills\clasp-setup" "$env:USERPROFILE\.agents\skills\clasp-setup"
Remove-Item -Recurse -Force "$env:TEMP\clasp-gas-skill"
```

### 步驟三：老師做的兩件事

跟老師說明後執行：

1. 提醒老師打開 <https://script.google.com/home/usersettings>，用**任教的學校帳號**登入，把「Google Apps Script API」切成開啟（跟他說「這是讓 AI 能替你上傳程式碼的開關」），**告訴他要等 1～2 分鐘生效**。
2. 執行登入，並先講清楚「等一下瀏覽器會打開，請用你**任教的學校帳號**登入、按允許」：

```powershell
clasp login
```

若對話環境無法互動開出瀏覽器，比照 [14-MCP-GitHub](14-MCP-GitHub.md) 的做法另開視窗：

```powershell
Start-Process powershell -ArgumentList "-NoExit","-Command","clasp login"
```

驗證：

```powershell
clasp show-authorized-user --json
```

看到帳號才算成功。回 `admin_policy_enforced` → **不要重試**，直接停下並請老師聯絡學校 Google 系統管理員（秘書）處理，本步驟先中止等老師回報。

### 步驟四：取得 classroom-tools 並建立 Apps Script 專案（要老師同意）

```powershell
git clone https://github.com/mathruffian-dot/classroom-tools.git "$env:USERPROFILE\Documents\classroom-tools"
cd "$env:USERPROFILE\Documents\classroom-tools"
Test-Path ".clasp.json"
```

`.clasp.json` 已存在 → 先問老師這是不是他要接的專案，不要直接蓋掉。不存在的話，建立獨立的 Apps Script 專案並把程式推上去：

```powershell
clasp create-script --type standalone --title "Classroom自動化工具"
clasp push
```

`appsscript.json` 已經內附 Classroom 進階服務與所需的 OAuth 範圍，不需要老師額外設定。

### 步驟五：老師本人完成首次授權（老師在瀏覽器裡點）

跟老師說：「接下來會打開 Apps Script 編輯器，請在上方函式選單選 `listCourses`，按執行，Google 會跳出授權視窗，選你剛剛登入的學校帳號並同意」，然後打開編輯器：

```powershell
clasp open-script
```

老師執行完之後，請他把「執行記錄」裡列出的課程名稱與 id 念給你聽（或截圖），你才知道要針對哪個 `courseId` 操作。

**之後每次要貼公告、建作業、或查繳交狀況，固定流程**：

1. 問清楚老師這次要貼的公告文字／作業標題與說明／要查哪一門課。
2. 把 `Code.js` 裡對應的 `COURSE_ID` 與函式內文字改好，執行 `clasp push`。
3. 告訴老師去編輯器選對應函式（`postAnnouncement`／`createAssignment`／`exportSubmissionsToSheet`）按執行——**這一步一定要老師自己按**。
4. 老師執行完回報結果（或給你新試算表的網址／執行記錄截圖），你再往下協助（例如打開試算表幫忙整理）。

### 步驟六：驗證

```powershell
clasp show-authorized-user --json
Test-Path "$env:USERPROFILE\Documents\classroom-tools\.clasp.json"
```

加上老師已經成功執行過一次 `listCourses` 並把課程清單念給你聽，才算完整驗證通過。

### 步驟七：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 17 clasp Google Classroom（YYYY-MM-DD HH:MM）

- Node.js 版本：
- clasp 版本：
- clasp-setup 技能位置：~/.agents/skills/clasp-setup（Codex）／~/.claude/skills/clasp-setup（Claude Code）
- Apps Script API 開關：老師已開啟 / 待老師開啟
- clasp 登入帳號：<學校帳號> / 待老師登入 / 失敗（admin_policy_enforced）
- classroom-tools 專案位置：
- 首次 listCourses 執行：老師已完成 / 待老師執行
- 問題紀錄：<沒有就寫「無」>
```

### 步驟八：回報老師

用白話表格回報，**不要貼指令輸出原文**：

| 項目 | 結果 |
|---|---|
| clasp 本身 | ✅／❌ |
| clasp-setup 技能 | ✅／❌ |
| Apps Script API 開關 | ✅／⚠️ 待老師開啟／❌ |
| Classroom 帳號登入 | ✅／⚠️ 待老師登入／❌ 需聯絡系統管理員 |
| classroom-tools 專案已建立並推送 | ✅／❌ |
| 首次 `listCourses` 執行 | ✅／⚠️ 待老師去編輯器按執行 |

全部 ✅ 時，提醒老師：「之後要貼公告、建作業或查繳交狀況，我會先把內容準備好推上去，最後一步請你自己去 Apps Script 編輯器按執行——這是 Google 的安全機制，也順便幫你把關，按下去前請務必看過內容。學生名單或成績我只會在你明確要求時才列出，而且會盡量用座號。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Classroom 連接移除」時）

**先問老師一次再動作**：

1. 刪除技能資料夾：`~/.agents/skills/clasp-setup`（Codex）或 `~/.claude/skills/clasp-setup`（Claude Code）
2. 問老師是否要移除全域 clasp：`npm.cmd uninstall -g @google/clasp`
3. 清除本機登入狀態：`clasp logout`
4. `classroom-tools` 專案資料夾與 `.clasp.json`：問老師要不要保留（裡面記著他的 Apps Script 專案對應關係），預設不要動
5. Classroom 網站上的課程、公告、作業，以及雲端上的 Apps Script 專案本身**完全不要動**，那是老師自己在 Google 上的資料

---

## 已知限制

| 限制 | 說明 |
|---|---|
| 貼公告、建作業、查繳交狀況都要老師自己按「執行」 | Apps Script 函式的執行需要在編輯器裡用老師本人的 Google 授權觸發，clasp CLI 目前無法代為觸發，這是 Google 與 clasp 本身的限制，不是這包漏做 |
| AI 讀不到「執行記錄」的輸出 | clasp 沒有對應指令能直接抓 `Logger.log` 的內容，老師執行完要自己念出來或截圖，AI 才知道結果 |
| 只能操作 `Code.js` 裡寫好的 6 個函式 | `listCourses`／`listStudents`／`postAnnouncement`／`createAssignment`／`listCourseWork`／`exportSubmissionsToSheet` 以外的操作（例如修改或刪除作業、搜尋整個雲端硬碟、用程式建立或分享 Google 文件／試算表）原作 repo 沒有現成程式碼，**本包不含**，不會自己編一段湊數 |
| 學校網域帳號可能被管理員擋下 | `admin_policy_enforced` 老師自己解不了，需請學校 Google 系統管理員（秘書）將 OAuth Client 加入白名單，或確認 Classroom／Apps Script API 已開放 |
| 雲端硬碟自動化僅限已同步的資料夾 | 若要搜尋整個雲端硬碟、或用程式建立／分享 Google 文件與試算表，本包不含，需要另外開發 |
| 尚未實機測試 | 本包依原作 repo 的說明文件撰寫，**尚未在屏北高中研習電腦實際跑過一次完整安裝**，畫面若與實際不同以現場為準 |

## 來源與查證（2026-09-27）

- clasp-gas-skill（三師爸 Sense Bar 開發，MIT 授權）：<https://github.com/mathruffian-dot/clasp-gas-skill>（`README.md`、`AGENTS.md`、`skills/clasp-setup/SKILL.md`、`references/platform-notes.md`、`scripts/install.ps1`）
- classroom-tools（三師爸 Sense Bar 開發）：<https://github.com/mathruffian-dot/classroom-tools>（`README.md`、`Code.js`、`appsscript.json`）——本包選它當 Classroom 自動化主線，因為它是唯一涵蓋「把全課程繳交狀況匯出成試算表」的方案，且直接沿用 clasp-setup 已建立的登入與推送流程
- 另有 classroom-agent-kit（Node.js 命令列工具，<https://github.com/mathruffian-dot/classroom-agent-kit>）可用終端機指令直接操作 Classroom、不需要 clasp，但要老師另外在 Google Cloud Console 建立獨立的 OAuth 桌面應用程式憑證（`credentials.json`），且不含繳交狀況匯出功能，本包未採用
- `@google/clasp` 最新版 3.4.1（npm）
- Codex 官方個人技能資料夾為 `~/.agents/skills`（見本專案 AGENTS.md 注意事項；`$skill-installer` 裝到 `~/.codex/skills` 官方文件未列出）
