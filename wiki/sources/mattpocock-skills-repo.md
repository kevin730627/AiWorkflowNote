---
type: source
tags:
  - ai-skills
  - claude-code
  - prompt-engineering
  - software-engineering
created: 2026-10-19
updated: 2026-10-19
raw: raw/介紹 Skills 專案.md
author: ChatGPT 對話紀錄
published: 2026-10-18
url: https://chatgpt.com/c/6ad5afec-5c04-83ee-819f-7fa10f3ffb7c
---

# 介紹 Skills 專案

## 一句話摘要
詳細拆解 [[Matt Pocock]] 開源的 `mattpocock/skills` 專案架構，涵蓋五大類工程化 Skill 指令集、與 `CLAUDE.md` 的靜態背景/動態流程互補關係，以及透過 CLI 安裝與漸進式採用的實踐策略。

## 重點
- **專案本質定位**：非獨立模型或應用，而是寫在 [[Markdown]] 指令文件（如 `SKILL.md`）中的技能集合，旨在替 AI 程式代理（如 [[Claude Code]]）安裝資深工程師的工作方法與工程紀律。
- **五大技能分類體系**：
  1. **需求分析與規劃**：`grill-me`、`grill-with-docs`、`to-spec`、`to-tickets`（在寫 code 前釐清盲點，產出無代碼 spec 與垂直 tickets）。
  2. **[[TDD|測試驅動開發 (TDD)]]**：`tdd`、`implement`、`implement-spec`（以紅燈-綠燈-重構循環引導實作，杜絕 AI 偽造測試）。
  3. **除錯與程式碼審查**：`diagnosing-bugs`（先重現問題、縮小範圍，以證據驅動除錯）、`code-review`（檢查代碼品質與壞味道）。
  4. **架構與程式碼改善**：`domain-modeling`、`codebase-design`、`improve-codebase-architecture`（領域概念建模、改善模組邊界、深模組治理）。
  5. **專案管理與工作流程**：`ask-matt`、`triage`、`retro`、`research`（流程選擇、任務分類、復盤回顧）。
- **[[專案規則與技能工作流]]（`CLAUDE.md` vs `SKILL.md`）**：
  - `CLAUDE.md` 負責「專案的長期靜態規則與背景」（命名慣例、架構原則、技術棧限制）。
  - `SKILL.md` 負責「特定工作的動態操作流程」（規劃、測試、除錯、重構步驟）。
  - 兩者為互補關係，可搭配協同使用。
- **安裝與漸進式導入**：
  - 透過 `npx skills@latest add mattpocock/skills` 安裝，並以 `/setup-matt-pocock-skills` 進行初始化設定（可指定 Issue Tracker 如 GitHub、Linear 或本地檔案）。
  - 建議先從核心模組（需求分析、TDD、除錯、架構）循序漸進引入，避免一次全數載入造成混亂。

## 值得注意的細節或數據
- 專案 repository 為 `https://github.com/mattpocock/skills`。
- 技能調用機制可依照使用者手動呼叫或 Skill 設定的條件觸發。
- 第三方 Skill 指令集具有修改開發環境之權限，導入前需審視其檔案與權限操作。

## 與既有 wiki 的關係
- **補充**：本篇對 [[grill-me-matt-pocock]] 的概念進行了具體的工具庫盤點，將其散落在影片中的技巧結構化為五大技能類別，並明確了與 `CLAUDE.md` 的職責劃分。

## 提及的實體與概念
- 實體：[[Matt Pocock]]、[[Claude Code]]
- 概念：[[專案規則與技能工作流]]、[[Skill 設計原則]]、[[grill-me]]、[[深模組與淺模組]]、[[TDD]]
