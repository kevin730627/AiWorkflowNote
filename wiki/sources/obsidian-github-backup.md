---
type: source
tags:
  - obsidian
  - note-taking
  - local-first
  - git
  - ai-workflow
created: 2026-10-19
updated: 2026-10-19
raw: raw/AI 時代最好用的筆記軟件 Obsidian，從零開始安裝 Obsidian 並使用 Github 同步和備份.md
author: ankmak
published: 2026-03-25
url: https://ankmak.com/tech/2026/03/25/use-obsidian-and-sync-backup-via-github.html
---

# AI 時代最好用的筆記軟件 Obsidian，從零開始安裝 Obsidian 並使用 Github 同步和備份

## 一句話摘要
介紹 [[Obsidian]] 的[[本地優先]]理念與 [[Markdown]] 純文字優勢，並詳述如何透過 Git 與 GitHub 私有儲存庫實現跨平台自動備份，以及利用 [[Gemini CLI]] 在本機終端機進行 AI 知識庫共編。

## 重點
- **[[Obsidian]] 的本質與價值**：Obsidian 本質為純文字檢視器，筆記庫（Vault）即本地資料夾；採用「[[本地優先]]（Local-first）」架構，筆記永遠屬於自己，杜絕服務商鎖定風險。
- **[[Markdown]] 在 AI 時代的優勢**：身為純文字格式，Markdown 能被主流 AI 模型（如 Gemini, GPT-4）無縫解析與生成，天然適合作為第二大腦與 AI 協作的通用資料格式。
- **跨裝置同步方案對比**：
  - iCloud Drive（適用 Apple 生態，簡單但有跨平台限制）。
  - Synology NAS + Remotely Save（WebDAV 協議，適合高度自建隱私需求）。
  - 官方 Obsidian Sync（穩定方便但需付費訂閱）。
  - **Git + GitHub Private Repo**（免費、兼具版本歷程回溯與私密安全，為作者首選方案）。
- **Git 同步實作指引**：
  - Vault 根目錄設定 `.gitignore` 排除頻繁變動的工作區狀態（`.obsidian/workspace*.json`、`.DS_Store`）。
  - 安裝 `Obsidian Git` 社群外掛，啟用自動 commit & sync（閒置 1 分鐘備份）與啟動時 auto pull。
  - iOS 同步因沙盒限制，需透過 GitHub Personal Access Token (PAT，勾選 `repo` 權限、無過期限制) 授權 Obsidian Git 內建核心進行 clone 與同步。
- **終端機 AI 工具深度整合**：因檔案存於本機，可直接透過 [[Gemini CLI]] 呼叫 AI 進行單篇筆記摘要、批次靈感整合與知識圖譜建議，讓 AI 成為檔案層級的共創夥伴。

## 值得注意的細節或數據
- 自動備份設定建議：間隔設為 1 分鐘，並開啟「停止編輯後自動 commit-and-sync」與「啟動時 pull」。
- iOS 同步無法使用傳統 SSH Key，必須在 GitHub 申請 Classic PAT（權限僅需 `repo`）。
- 排除 `.obsidian/workspace.json` 可大幅減少跨裝置工作區切換時的無謂版本衝突。

## 圖片觀察
- `20260326084712606.png`（封面視覺）：Obsidian 紫水晶圖示居中，四周環繞 Markdown 標記符號（`#`、`md`、`[]`、`*`）；左側連結 GitHub（標註 Sync & Backup、`git push`、`backup.sh`），右側連結 Gemini CLI 終端機（標註 AI Integration & Analysis、`gemini cli connect`、`query_response`）。視覺化呈現出「本地存儲為核心、雲端 Git 保版本、終端 AI 做分析」的閉環架構。
- `20260326084802471.png` 與 `20260326084811460.png`（Markdown 源碼與渲染對照）：範例檔案 `sample.md` 展示了標題、列表、引文、Python 代碼塊（平方計算函數）以及 LaTeX 二次方程式公式。前者展示純文字編輯狀態，後者展示 Obsidian 渲染後的乾淨閱讀排版。
- `donate.png`（贊助圖）：作者在文末提供的微信支付與支付寶贊助收款 QR Code。

## 與既有 wiki 的關係
- **補充**：本 wiki 本身即為一個 Obsidian Vault，本來源說明了此種「本機 Markdown 資料夾 + Git 版本控制」正是 LLM 能夠直接作為檔案層級共編者（如當前維護此 wiki）的基礎設施與底層原理。

## 提及的實體與概念
- 實體：[[Obsidian]]、[[Gemini CLI]]
- 概念：[[本地優先]]、[[Markdown]]
