# 屏北高中 Agent 基本功懶人包 #18：連接 Firebase 資料庫

> 版本：v1.0｜更新日期：2026-09-27
> 適用：**Codex Desktop**（主要）；Claude Code 附差異說明
> 對應教材：**A9 HTML 互動簡報的延伸挑戰**（即時文字雲、投票）；知識點總表列為**選修**
> 改作來源：三師爸 Sense Bar 的 Codex 懶人包《04.5 連接 Firebase 資料庫》（[codex-lazy-packs](https://github.com/mathruffian-dot/codex-lazy-packs)，MIT）
> 狀態：🟡 依三師爸懶人包改寫，使用者實測可安裝；本版格式尚未在研習電腦重測

> 🤖 **AI Agent 請注意**：老師不熟指令。請直接跳到文末「[給 AI Agent 的執行步驟](#給-ai-agent-的執行步驟老師不用看這段)」，照那一節由你自己執行。

---

## 這包做什麼

**研習必修不需要這包。** A9 做的 HTML 互動簡報本身不需要資料庫；只有想在簡報裡加「學生即時輸入文字雲」「課堂即時投票」這類需要多人同時寫入、馬上看到結果的功能，才需要裝這包連上 Firebase 資料庫。沒有這個需求就跳過。

裝好之後，你可以直接跟 AI 說：

| 你說 | AI 會做 |
|---|---|
| 「做一個即時文字雲，連接 Firebase」 | 產前端網頁 + 連 Firestore 資料庫 + 學生輸入後即時更新畫面 |
| 「做課堂投票工具」 | 產網頁 + 改 Firestore 安全規則 + 自動部署 |
| 「查最熱門的 5 個關鍵字」 | 直接讀資料庫統計給你看 |
| 「刪掉所有測試資料」 | 清空測試用的資料 |

---

## ⚠️ 先確認

- **只需要 Google 帳號，不用付費**（Firebase 免費方案 Spark 就夠用，見文末「已知限制」）。
- 這兩步要老師自己**用瀏覽器**做，AI 沒辦法代勞（是操作 Google 網頁介面）：
  1. 到 <https://console.firebase.google.com> → 建立專案（名稱自訂，例如 `my-teaching-tools`；Google Analytics 可不啟用）
  2. 進專案 → **Firestore Database** → 建立資料庫 → 選 **Standard 版**、地區選 `asia-east1 (Taiwan)` 或 `asia-northeast1 (Tokyo)`、**安全性規則選「以正式版模式啟動」**（**不要選測試模式**，測試模式 30 天會自動過期，屆時整個資料庫會讀不到）

兩步都做完 → 繼續往下貼指令給 AI。

---

## 怎麼裝：貼一段話給 AI

**老師不用打任何指令。** 只要做這幾件事：

1. 打開 **Codex Desktop**
2. 把下面這段話**整段複製、貼上、送出**
3. AI 要動到電腦時會跳出確認，**看一眼、按同意**
4. AI 會**另外跳出一個新視窗**請你完成 Firebase 登入——這是**瀏覽器登入你的 Google 帳號**，不是貼金鑰，**跟平常登入 Google 一樣**
5. AI 說「請重開」時，把 Codex **整個關掉再打開**（右下角系統匣的 Codex 圖示也要按結束），然後**再貼一次同一段話**

```text
請讀取 https://raw.githubusercontent.com/frentexx/ppsh-agent-basics-packs/main/18-MCP-Firebase.md
照其中「給 AI Agent 的執行步驟」，幫我把 Firebase 連接裝好。
我不熟指令：請你自己判斷、自己執行，需要我同意的地方跳出確認就好，不要叫我自己打指令。
全部做完後，用一張簡單的表告訴我結果，以及我接下來要做什麼。
```

**裝到一半失敗**：不用自己修，把 AI 最後給你的結果表**截圖給研習講師**。

---

## 裝好之後：驗收

重開 Codex，跟它說：

```text
幫我列出 Firebase 專案，然後列出 Firestore 集合，接著新增一筆 test_collection 測試資料，再讀回來，最後刪掉。
```

看到「連接測試成功」（AI 依序列出專案、集合，新增、讀到、刪掉都成功）就代表裝好了。

---

## 已知限制

| 項目 | 說明 |
|---|---|
| 免費額度（Spark 方案） | 儲存 1 GB／讀取 50,000 次天／寫入 20,000 次天；專案數**無限**；**不會**閒置暫停 |
| `firestore_query_collection` 可能回 `read_time cannot be in the future` | 這是 MCP 查詢工具的已知問題。要驗證資料庫能讀寫，先改用「讀單筆」「列出所有文件」這兩個功能 |
| 集合路徑不可以有結尾斜線 | 例如要寫 `wordcloud_words`，不要寫成 `wordcloud_words/` |
| 新增文件的格式 | AI 要用 Firestore 的文件物件格式寫入，不是把資料包成一整串文字塞進去；這件事由 AI 處理，老師不用管 |
| 選了「測試模式」的安全規則 | 30 天後會自動失效，資料整個讀不到。本包一律用「正式版模式」＋白名單規則（見執行步驟） |
| `firebase login` 在 AI 對話裡卡住 | 已在執行步驟改成開獨立視窗完成，不會卡在對話裡 |
| Windows 上 `npx` 出錯 | 一律改用 `npx.cmd`（本包指令都已經這樣寫） |

---

## 安全提醒

- Firebase 網頁前端用的 **Config（`apiKey` 等）本身是設計給公開網頁用的，可以放進網頁程式碼**——真正的門鎖是**資料庫的「安全規則」（Security Rules）**，沒設好等於任何人都能讀寫全部資料。
- 本包預設只開放你指定的**單一集合**（例如 `wordcloud_words`）讓任何人讀寫，是**課堂 demo 用的權宜規則**。活動結束或要正式長期使用，記得請 AI 把規則收緊（例如限制班級、限制時間、要求登入）。
- **絕對不要建立或使用 Firebase 服務帳戶金鑰（service account JSON／private key）**，本包全程只用老師自己的 Google 帳號登入，用不到這種金鑰；如果專案資料夾裡不小心出現這種檔案，**不要放進要推上 GitHub 的資料夾**。
- 學生寫進文字雲、投票的內容**不要求填真名**，用座號或匿名即可。
- 登入全程在老師自己的瀏覽器完成，AI 看不到也不會問你帳號密碼。

---

## 給 AI Agent 的執行步驟（老師不用看這段）

> [!IMPORTANT]
> **安全與互動規則（請先讀完再動手）**
> 1. 老師**不熟指令**：**所有指令由你執行**，不要把指令或參數說明丟給老師、叫他自己打。
> 2. **只安裝本文件列出的項目**，不要自行追加其他套件、外掛或 MCP。
> 3. **會改動電腦或寫入檔案的步驟**（安裝、修改設定檔、寫入 Firestore 規則檔）：照你所在 Agent 的權限確認機制取得老師同意。
> 4. **只讀不改的檢查指令**可以直接執行。
> 5. **Firebase 登入靠瀏覽器的 Google 帳號授權，不是金鑰**：`firebase login` 完全由老師在跳出的瀏覽器頁面自己完成，你不需要、也不可以代填帳號密碼；不要讀取或顯示 `firebase-tools` 存放登入憑證的檔案內容（例如使用者設定目錄下的 `configstore`），只能檢查登入「有沒有成功」（例如能不能列出專案）。
> 6. **絕對不要建立、下載或使用 Firebase 服務帳戶金鑰（service account JSON / private key）**，本包全程只走老師自己的 Google 帳號登入。若老師的資料夾已存在這類金鑰檔，提醒他不要放進要推上 GitHub 的資料夾，不要自己去讀取或搬動它。
> 7. 寫入 `firestore.rules` 時**只用本文件提供的白名單範例**（測試 demo 用），部署前先跟老師確認要開放的集合名稱；不要自己發明其他規則邏輯，也不要把規則寫成對所有集合全開。
> 8. 不要刪除、搬動或修改老師的其他檔案；改 `config.toml` 前一定先備份；可以重複執行，已完成的項目檢查通過就跳過；遇到錯誤先停下來用白話說明，**不要換成本文件以外的方法硬裝**。

### 步驟一：檢查（只讀，直接執行）

```powershell
node --version
git --version
npx.cmd -y firebase-tools@latest --version
Select-String -Path "$env:USERPROFILE\.codex\config.toml" -Pattern '^\[mcp_servers\.firebase\]' -Quiet
```

| 項目 | 狀態 |
|---|---|
| Node.js、Git | 有版本號才算有（沒有 → 請老師先做 [00 環境檢查](00-環境檢查與基礎工具.md)，本包停止） |
| firebase-tools 可執行 | 有版本號才算有 |
| Codex 設定已加入 | `True`／`False` |

PowerShell 回「因為這個系統上已停用指令碼執行」→ 之後的 `npm` 一律改用 `npm.cmd`（本步驟只用到 `npx.cmd`，通常不受影響）。

再檢查登入狀態（只讀）：

```powershell
npx.cmd -y firebase-tools@latest projects:list
```

能列出至少一個專案 → 已登入，跳到步驟三；回報要求登入或空清單 → 進步驟二。

### 步驟二：登入 Firebase CLI（要老師同意；登入本身不經過你）

跟老師確認過「先確認」段落兩步驟都做完後，開一個獨立視窗讓老師自己完成登入：

```powershell
Start-Process powershell -ArgumentList "-NoProfile", "-Command", "npx.cmd -y firebase-tools@latest login; Read-Host '登入完成後按 Enter 關閉這個視窗'"
```

跟老師說：「我開了一個新視窗，會自動跳出瀏覽器，請用你要綁定 Firebase 專案的 Google 帳號登入，完成後回到這裡跟我說『好了』。」

老師說好了之後，用這行確認（**不要顯示任何憑證檔案內容**）：

```powershell
npx.cmd -y firebase-tools@latest projects:list
```

能列出專案才算成功；仍然失敗就停下來，跟老師說明第一行錯誤訊息。

### 步驟三：確認要用的 Firebase 專案（只讀＋跟老師確認）

把上一步 `projects:list` 列出的專案名稱／ID（不是機密資訊，可以直接顯示）念給老師聽，請老師指出「先確認」段落裡建立的那個專案要用哪一個，記下它的**專案 ID**（後面步驟要用）。

### 步驟四：建立並部署 Firestore 安全規則（要老師同意；會寫入檔案）

在老師目前的專案資料夾建立三個檔案：

**1. `firestore.rules`**（把 `wordcloud_words` 換成老師這個功能實際會用到的集合名稱，跟老師確認後再定案）：

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /wordcloud_words/{document} {
      // 測試用公開白名單：只適合課堂 demo，不可直接用在正式學生資料或長期公開服務。
      allow read, write: if true;
    }
    match /{document=**} {
      allow read, write: if false;
    }
  }
}
```

**2. `firebase.json`**：

```json
{
  "firestore": {
    "rules": "firestore.rules"
  }
}
```

**3. `.firebaserc`**（`[專案ID]` 換成步驟三確認的那個）：

```json
{
  "projects": {
    "default": "[專案ID]"
  }
}
```

部署規則：

```powershell
npx.cmd -y firebase-tools@latest deploy --only firestore:rules
```

看到 `Deploy complete!` 才算成功；之後要開放新集合（例如投票工具的 `votes`），在 `firestore.rules` 加一段類似的白名單、重跑這行部署即可，並提醒老師正式服務要收緊規則。

### 步驟五：加進 Codex 設定（要老師同意）

**你是 Codex**：先備份，再把區塊**附加到 `config.toml` 最後面**（已有 `[mcp_servers.firebase]` 就不要重複加，改為檢查內容是否與下面一致）：

```powershell
$cfg = "$env:USERPROFILE\.codex\config.toml"
Copy-Item $cfg "$cfg.bak-$(Get-Date -Format yyyyMMdd-HHmm)"
$block = @"

# 屏北高中懶人包 #18：Firebase（登入資訊由 Firebase CLI 自行保管，這裡不寫任何金鑰）
[mcp_servers.firebase]
command = "npx.cmd"
args = ["-y", "firebase-tools@latest", "mcp"]
startup_timeout_sec = 60
tool_timeout_sec = 120
"@
[IO.File]::AppendAllText($cfg, $block, (New-Object Text.UTF8Encoding $false))
```

- 設定檔本身不含任何金鑰或帳密，登入憑證由 `firebase-tools` 自己保管在使用者設定目錄。
- 設定檔開頭若有 `NMKING MANAGED CONFIG` 字樣：照樣附加在最後面即可。要提醒老師：**之後若重新套用 NMK 連線設定，這段會被蓋掉，再貼一次本包那段話就好**。

**你是 Claude Code**（未實測）：

```powershell
claude mcp add firebase --scope user -- npx -y firebase-tools@latest mcp
```

### 步驟六：驗證

**剛改完設定或剛登入**：這個對話還看不到 firebase 工具。
→ 請老師**完全結束 Codex**（含系統匣圖示）後重開，**再貼一次同一段話**。

**重開後再次執行本文件時**：

1. 步驟一三項都應為成功
2. 跟 AI 說「幫我列出 Firebase 專案，然後列出 Firestore 集合，接著在 `test_collection` 新增一筆 `message` 為『Firebase 連接測試成功』的資料，再讀回來，最後刪掉，並確認刪除後讀不到。」全部成功才算過
3. 看不到 firebase 工具 → 請老師到 Codex **設定 → MCP servers** 看 `firebase` 是否啟用、有無錯誤訊息
4. 讀寫失敗、出現權限錯誤 → 確認步驟四的安全規則有沒有部署成功、集合名稱是否對得上

### 步驟七：更新環境檢查報告

在目前資料夾的 `環境檢查報告.md` 最上方加一段（沒有就新建）：

```markdown
## 18 Firebase（YYYY-MM-DD HH:MM）

- Firebase 專案：<專案 ID>
- firebase-tools：可執行 / 失敗
- 登入狀態：已登入 / 未登入
- Firestore 安全規則：已部署 / 失敗 / 尚未建立
- Codex 設定：已加入 / 失敗
- 連線測試：成功（列出／新增／讀取／刪除皆通過）/ 待重開後驗證 / 失敗
- 問題紀錄：<沒有就寫「無」>
```

### 步驟八：回報老師

用白話表格回報，**不要貼指令輸出原文、不要顯示任何憑證內容**：

| 項目 | 結果 |
|---|---|
| Firebase 專案 | ✅ `<專案 ID>`／❌ |
| Firebase CLI 登入 | ✅ 已登入／⚠️ 還沒完成 |
| Firestore 安全規則 | ✅ 已部署／❌ |
| Codex 設定 | ✅／❌ |
| 連線測試 | ✅ 成功／⚠️ 要重開後再貼一次／❌ |

最後明確告訴老師下一步，例如：
「請把 Codex **整個關掉再打開**（右下角系統匣也要結束），然後**再貼一次同一段話**，我會幫你做連線測試。」並提醒：「這個規則是課堂 demo 用的公開白名單，正式給學生用之前要跟我說一聲，我幫你收緊規則。」

有任何一項 ❌：說明卡在哪一步、錯誤訊息第一行，請老師**截圖給研習講師**。

---

## 復原（老師說「把 Firebase 連接移除」時）

1. 從 `config.toml` 刪掉 `# 屏北高中懶人包 #18` 那一段（先備份）
2. 提醒老師：資料庫本身、Firestore 資料、Firebase 專案都不會被這個動作刪掉，要在 Firebase Console 自己處理
3. 登出 CLI：

```powershell
npx.cmd -y firebase-tools@latest logout
```

---

## 來源與查證（2026-09-27）

- 內容改寫自三師爸 Sense Bar《Codex 懶人包 #04.5：連接 Firebase 資料庫》（MIT，[codex-lazy-packs](https://github.com/mathruffian-dot/codex-lazy-packs)），使用者實測可依原作指令安裝成功
- 原作用的是 **Firebase CLI（`firebase-tools`）＋其內建的 MCP 子指令（`firebase-tools mcp`）**，不是獨立的第三方 MCP 套件
- [Firebase 官網](https://firebase.google.com)
- [Firebase MCP Server 文件](https://firebase.google.com/docs/ai-assistance/mcp-server)
- [Codex MCP 官方文件](https://developers.openai.com/codex/mcp)
