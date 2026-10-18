---
title: "AI 時代最好用的筆記軟件 Obsidian，從零開始安裝 Obsidian 並使用 Github 同步和備份"
source: "https://ankmak.com/tech/2026/03/25/use-obsidian-and-sync-backup-via-github.html"
author:
published:
created: 2026-10-18
description: "前言如果你希望：  你寫的筆記永不消失。  即使換了軟件，你的筆記可以很輕鬆的轉移到其它工具上。  把筆記本作為第二大腦  可以與各大 AI 結合使用  可以輕易發佈到 Website不用再尋找了，也不用再換來換去了，Obsidian 就是最終答案。"
tags:
  - "clippings"
---
![[20260326084712606.png|Gemini_Generated_Image_36vlbw36vlbw36vl.png]]

## 前言

如果你希望：

- 你寫的筆記永不消失。
- 即使換了軟件，你的筆記可以很輕鬆的轉移到其它工具上。
- 把筆記本作為第二大腦
- 可以與各大 AI 結合使用
- 可以輕易發佈到 Website

不用再尋找了，也不用再換來換去了， **Obsidian 就是最終答案** 。

## 1\. 首先要知道 Markdown 是什麼？

A: Markdown 是一種非常輕量級的「標記語言」（Markup Language），用最普通的純文字格式來編寫文件，透過加入一些簡單的符號，就能讓文字具備標題、粗體、清單或插入程式碼等排版效果。它最終可以非常輕鬆地轉換成 HTML 網頁格式。看看例子：

這是寫出來的

![[20260326084802471.png|截圖 2026-03-25 22.55.23.png]]

這是你看見的

![[20260326084811460.png|截圖 2026-03-25 22.58.37.png]]

## 2\. 為什麼在 AI 時代，Obsidian 是你最值得投資的筆記工具？

- **Markdown 的通用性：** Markdown 是一種純文字格式，幾乎所有的 AI 模型（如 Gemini, GPT-4）都能完美解析並生成這種格式。這意味著你的筆記天然地與 AI 相容。
- **數據主權與隱私：** 你的所有筆記都以 Markdown 格式儲存在你自己的硬碟上。在 AI 時代，個人資料的私隱性尤為重要，你不需要擔心服務商倒閉或數據外洩。
- **強大的插件生態：** 透過社群開發的插件，你可以將 Obsidian 轉化為任務管理工具、繪圖工具，甚至是你的個人 AI 助手介面。

簡單來說，Obsidian 就只是一個把 XXX.md 的純文字記事本打開的軟件。

但它強大的地方是它的核心理念是「本地優先（Local-first）」，也就是所有的筆記都是以最基本的 **Markdown** 純文字檔案儲存在你的裝置硬碟裡。也就是說當有一天你不再用 Obsidian， **你的筆記仍然是屬於你的** 。

## 3\. 從零開始：下載與安裝 Obsidian

安裝過程非常直覺：

1. 前往 [Obsidian 官網 (obsidian.md)](https://obsidian.md/) 。
2. 根據你的作業系統（macOS, Windows, 或 Linux）下載對應的安裝檔。
3. 執行安裝程式並啟動軟體。

啟動 Obsidian 後，系統會要求你建立或開啟一個「庫」(Vault)。

- **什麼是庫 (Vault)？** 簡單來說，一個庫就是電腦上的一個 **資料夾** 。
- **資料夾即筆記庫：** Obsidian 只是這個資料夾的「檢視器」。這意味著你可以用任何其他的文字編輯器、終端機工具（如 Gemini CLI）來操作這些檔案，而不會被特定軟體綁架。

## 4\. 如何同步/備份筆記

由於前面一直強調筆記是存放在本地上，因此代價是相對於市面上的其他筆記軟件，它失去了由伺服器來管理筆記的便利。

相對的，筆記要實現跨裝置同步和備份就需要自己稍微花點心思進行設定，目前大概有以下幾種方法：

1. 透過 iCloud Drive (最適合蘋果生態系)
	- 設定簡單，只需在 iCloud Drive 中建立一個資料夾作為你的 Obsidian Vault
2. 透過 Synology NAS 打造私人同步中心 (適合重視隱私與資料掌控)
	- 在 NAS 上開啟 WebDAV Server 功能。接著在 Obsidian 內安裝社群外掛（Community Plugin） **「Remotely Save」** ，資料完全私有化。
3. 使用 Git 進行版本控制
	- 擁有完美的版本控制歷史，改錯了隨時可以回溯
4. 官方的 Obsidian Sync
	- 設定最無腦，且包含完整的版本歷史紀錄，唯一缺點需要每月/每年付費訂閱。

經過一番比較後我選擇了使用 Git，搭配 Github Private Repo 儲存庫，同時獲得版本控制和資料私密的好處。

### 第一步：在 GitHub 建立儲存庫

1. 登入 GitHub，點擊「New repository」。
2. 命名為 `obsidian-vault` （或你喜歡的名字）， **務必設為 Private** 以保護筆記隱私。
3. 不要勾選「Add a README」或「.gitignore」，保持一個完全空的 Repo。

### 第二步：將 Mac 本地端與 GitHub 連結

#### 1.建立.gitignore 檔案（強烈建議）

Obsidian 會在 `.obsidian` 資料夾中產生一些本機端的工作區狀態（例如你目前開啟了哪些分頁），這些頻繁變動的檔案不需要被 Git 記錄。請在 Vault 根目錄建立一個名為 `.gitignore` 的檔案，並寫入以下內容：

```bash
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.DS_Store
```

#### 2.在 Mac 終端機（Terminal）初始化：

依序執行以下指令，將筆記推送到 GitHub：

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
# 將下方的 URL 換成你的 GitHub Repo 連結
git remote add origin https://github.com/你的帳號/obsidian-vault.git
git push -u origin main
```

### 第三步：安裝 Obsidian Git 插件

- 回到 Mac 的 Obsidian，進入「設定」 > 「第三方外掛程式」，關閉安全模式。
- 點擊「瀏覽」，搜尋並安裝 **「Git」** ，然後將它啟用。
- 進入 Obsidian Git 的設定頁面，設定自動備份機制：
	- **Auto commit-and-sync interval (minutes):** 設定為 `1` ，即每分鐘自動備份一次。
		- **Auto commit-and-sync after stopping file edits:** 開啟此選項，確保閒置 1 分鐘後自動備份。
		- **pull on startup:** 開啟此選項。這確保你每次在 Mac 打開 Obsidian 時，都會自動從 GitHub 拉取最新進度。

## 5\. AI 加持：將 Gemini CLI 深度集成到你的 Obsidian 工作流

這是 Obsidian 最令人興奮的部分。由於筆記本質上是 Markdown 檔案，我們可以直接在終端機利用 **Gemini CLI** 來處理這些內容。

### 如何集成？

1. **安裝 Gemini CLI：** 確保你的系統已安裝並設定好 Gemini CLI 環境。
2. **直接呼叫 AI：** 打開終端機，切換到你的筆記目錄。你可以執行類似這樣的指令：
	```bash
	gemini "幫我摘要這篇筆記：2026-03-25-Obsidian.md"
	```
3. **批次處理：** 如果你有大量的靈感碎片，可以利用 Gemini CLI 寫一個簡單的腳本，自動讀取當天的筆記並生成一份週報或知識圖譜建議。

這種「檔案層級」的互動，讓 AI 真正成為了你知識庫的共編者。

## 6\. iPhone 同步

iOS 系統有較嚴格的沙盒（Sandbox）限制，無法直接跑終端機指令，但 Obsidian Git 外掛內建了輕量級的 Git 核心，可以幫我們完成設定。

### 1\. 先取得 GitHub Personal Access Token (PAT)

要在 iOS 系統上進行 Git 操作，無法使用常規的 SSH Key 驗證，我們需要一組授權密碼（Token）讓手機端可以順利登入 GitHub。

1. 在網頁版 GitHub 點擊右上角大頭貼 > `Settings` 。
2. 滾動到最下方，點擊左側的 `Developer settings` > `Personal access tokens` > `Tokens (classic)` 。
3. 點擊 `Generate new token (classic)` 。
4. 名稱可以隨意填寫（例如： `Obsidian-iOS-Sync` ），過期時間（Expiration）建議設為 `No expiration` 避免日後突然無法同步。
5. **Scopes（權限）：** 只要勾選 `repo` （Full control of private repositories）即可。
6. 點擊 Generate 後， **立刻將那一串 Token 複製起來** （離開頁面後就看不到了，可以先暫存在記事本）。

### 2.在 iPhone 上設定拉取與同步

1. **建立暫存筆記本：** 在 iPhone 上打開 Obsidian App，先隨意建立一個「全新的空筆記本」（例如命名為 `TempVault` ）。
2. **安裝外掛：** 在這個空的筆記本中，進入設定安裝並啟用 **「Obsidian Git」** 外掛。
3. **複製遠端儲存庫：**
	- 關閉設定回到空白筆記，向下滑動螢幕（或點擊選單）叫出 **命令面板 (Command Palette)** 。
		- 輸入並執行 `Obsidian Git: Clone an existing remote repo` 。
		- 系統會要求你輸入 Repository URL，貼上你的 GitHub `.git` 網址。
4. **進行身分驗證：**
	- 接著系統會跳出視窗要求輸入 Username（你的 GitHub 帳號）。
		- 然後要求輸入 Password。 **這裡請貼上剛剛在第二階段取得的 Personal Access Token (PAT)** ，絕對不要輸入你原本的 GitHub 密碼。
5. **切換到正式筆記本：**
	- Clone 完成後，外掛會把 GitHub 上的筆記本下載到 iPhone 裡。
		- 這時點擊 Obsidian 左下角的「打開其他 Vault」圖示，你就會看到剛剛從 GitHub 下載下來的筆記本資料夾，點擊進入即可，剛剛那個 `TempVault` 就可以刪除了。

## 7\. 結語

其實這個部落格網站從建成之前我便已經使用 markdown 格式來撰寫文章，當初我就是喜歡 Markdown 易於管理和儲存的特性才選擇它。加上今年 AI Agent 爆發的年代，甚至讓我看見 Markdown 將會成會主流的可能性。

選擇 Obsidian 其實是選擇了一種「將掌控權還給自己」的數位生活方式。也許有一天我不再使用 Obsidian，但是我用

希望你能從今天開始，打造一個永不遺失且充滿智慧的第二大腦。

![[donate.png|donate]]