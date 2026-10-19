---
type: overview
tags:
  - overview
created: 2026-10-19
updated: 2026-10-19
sources:
  - grill-me-matt-pocock
  - obsidian-github-backup
  - mattpocock-skills-repo
---

# 知識庫總覽

本知識庫依照 Andrej Karpathy 提出的「LLM Wiki」模式運作，將非結構化的原始來源資料（`raw/`）轉化為互相連結、具備脈絡與語意結構的知識網路（`wiki/`）。

## 目前全局理解

經過三篇原始來源的匯入與提煉，知識庫目前形成以下三個相互支撐的完整層次：

1. **底層數據基建（Local-first PKM Substrate）**：
   - 核心以 [[本地優先]]（Local-first）與 [[Markdown]] 純文字為根本。
   - 透過 [[Obsidian]] 的本機 Vault 結構搭配 Git 版本控制，建立兼具資料主權、抗廠商鎖定與回溯能力的知識庫底座，天然支援各類終端機 AI 工具（如 [[Gemini CLI]]、[[Claude Code]]）在檔案層級進行讀寫與共同維護。

2. **代理引導架構（Context & Skill Architecture）**：
   - 建立了 [[專案規則與技能工作流]] 的雙層分工模式：
     - **靜態長期規則**（如 `CLAUDE.md`、`AGENTS.md`）：錨定專案的不可變約束、技術棧限制與架構邊界。
     - **動態操作手續**（如 `SKILL.md`）：封裝各階段具體的可執行 SOP，依工作情境靈活調用。

3. **AI 工程化實踐（Taming AI with Software Engineering）**：
   - AI 開發的最大痛點在於隨機性與 Context Window 限制。
   - [[Matt Pocock]] 的開源專案將軟體工程經典智慧融入提示詞，建構了包含五大分類（需求規劃、TDD、除錯審查、架構治理、專案協調）的模組化工具庫。
   - 透過 [[grill-me]] 逆向拷問防範 Vibe Coding，透過 [[TDD]] 紅綠燈循環杜絕作弊，透過 [[深模組與淺模組]] 提升局部性以降低 AI 記憶負擔，並運用 [[Skill 設計原則]]（修剪、指引詞、明確完成標準）最大化調動現代高智能模型的先驗能力。

## 待解問題與探索方向

- [x] Ingest 第一篇：[[grill-me-matt-pocock]]（完成核心 Skill 與深模組概念提煉）
- [x] Ingest 第二篇：[[obsidian-github-backup]]（確立本地優先、Markdown 與知識庫基建原理）
- [x] Ingest 第三篇：[[mattpocock-skills-repo]]（盤點完整五大技能體系與 CLAUDE.md / SKILL.md 分工架構）
- [ ] 深度分析（Analyses 規劃）：
  - 探討將本 LLM Wiki 維護流程（Ingest, Query, Lint）封裝為一組可執行的專用 Skill 之可行性。
  - 撰寫 `Superpowers 與 Matt Pocock 技能體系比較` 的橫向深入分析。
- [ ] 實踐探討：
  - `diagnosing-bugs` 的假設驗證方法論在實際工程專案中的具體落地表現。
