---
type: entity
tags:
  - tool
  - pkm
  - markdown
created: 2026-10-19
updated: 2026-10-19
sources:
  - obsidian-github-backup
---

# Obsidian

一款基於純文字 Markdown 格式、採[[本地優先]]架構的個人知識管理（PKM）與雙向連結筆記工具。

## 重要事實
- **架構本質**：Obsidian 的筆記庫（Vault）本質上就是使用者本機硬碟中的一個普通資料夾，軟體本身僅是該資料夾的檢視與編輯器 ([[obsidian-github-backup]])。
- **資料主權與抗脆弱性**：所有內容以純文字 [[Markdown]] 檔案保存，不依賴雲端專有資料庫。即便日後停止使用該軟體，檔案依舊完整保存在本機，避免廠商鎖定（Vendor lock-in）([[obsidian-github-backup]])。
- **外掛生態與擴充**：具備龐大的社群外掛生態，例如可透過 `Obsidian Git` 實現與 GitHub 的定時版本控制同步，亦可透過 `Remotely Save` 搭配 WebDAV 實現私有雲備份 ([[obsidian-github-backup]])。
- **人機協同底座**：本機資料夾結構讓終端機工具、指令碼或大型語言模型（如 [[Gemini CLI]]、AI Agent）能直接在檔案層級讀取、修改與建構索引，成為構建個人 LLM Wiki 的理想載體 ([[obsidian-github-backup]])。

## 與其他實體、概念的關係
- 實踐了 [[本地優先]] 的核心哲學。
- 以 [[Markdown]] 作為筆記底層數據格式。
- 可與 [[Gemini CLI]] 等終端機 AI 工具深度整合，實現本機知識庫的自動化維護。

## 各來源怎麼說
- [[obsidian-github-backup]] 指出在 AI 時代，Obsidian 的本機純文字特質讓它天然與各大 AI 模型相容，是打造永不消失的「第二大腦」的最終答案。
