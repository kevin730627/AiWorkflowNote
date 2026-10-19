---
type: overview
tags:
  - overview
created: 2026-10-19
updated: 2026-10-19
sources:
  - grill-me-matt-pocock
  - obsidian-github-backup
---

# 知識庫總覽

本知識庫依照 Andrej Karpathy 提出的「LLM Wiki」模式運作，將非結構化的原始來源資料（`raw/`）轉化為互相連結、具備脈絡與語意結構的知識網路（`wiki/`）。

## 目前全局理解

- **知識庫基礎設施（底層基建）**：
  - 核心基於 [[本地優先]]（Local-first）與 [[Markdown]] 純文字。透過 [[Obsidian]] 的本地資料夾（Vault）架構，確保數據主權、隱私與無廠商鎖定。
  - 藉由 Git 與 GitHub 達成跨裝置自動同步與版本歷程管理，並讓終端機 AI 工具（如 [[Gemini CLI]]）及當前 AI Agent 能在檔案層級進行讀寫共編。
- **AI 開發與提示詞工程（上層工作流）**：
  - AI 開發的最大瓶頸在於隨機性與 Context Window 限制。隨意的「Vibe Coding」會導致架構腐敗。
  - [[Matt Pocock]] 提出了模組化積木工作流（對抗 [[Superpowers]] 的重型死流程），由 [[grill-me]] 逆向拷問需求，`to-spec` 確立無代碼規格書，`to-tickets` 按功能垂直拆分，最後以 TDD 鎖死 AI 作弊空間。
- **工程哲學的交集（局部性與控制權）**：
  - 不論是軟體程式碼（[[深模組與淺模組]]）或是個人筆記庫（[[本地優先]] + [[Markdown]]），核心都在於維持極高的「局部性（Locality）」與掌控權，讓人類穩坐架構師位置，同時在 AI 有限的視野內給予最清晰的脈絡。

## 待解問題與探索方向

- [x] Ingest 第一篇：[[grill-me-matt-pocock]]（完成核心 Skill 與架構概念提煉）
- [x] Ingest 第二篇：[[obsidian-github-backup]]（確立本地優先、Markdown 與知識庫基建原理）
- [ ] 探索並 Ingest 剩餘 `raw/` 來源文檔：
  - `raw/介紹 Skills 專案.md`
- [ ] 深入探討：`grill-with-docs` 的決策文件沉澱機制與 Obsidian 本地 LLM Wiki 運作模式之互補性。
- [ ] 後續比較：待分析 `介紹 Skills 專案.md` 中的 Skill 實作與 Matt Pocock 的設計原則是否有異同或擴展。
