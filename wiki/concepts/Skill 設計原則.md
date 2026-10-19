---
type: concept
tags:
  - prompt-engineering
  - ai-skills
  - best-practices
created: 2026-10-19
updated: 2026-10-19
sources:
  - grill-me-matt-pocock
  - mattpocock-skills-repo
---

# Skill 設計原則

由 [[Matt Pocock]] 在其開源專案 `mattpocock/skills` 中提出並實踐的高效 AI Agent Skill 設計理念與工程規範。

## 三大提示詞撰寫原則（Writing Great Skills）

### 1. 修剪（Pruning）
- **核心思想**：在 AI 面前多寫一句廢話，AI 就多一分分心的可能 ([[grill-me-matt-pocock]])。
- **實踐做法**：修剪所有冗言贅字，刪除即使不說模型也預設知道該如何執行的通用指令，確保 Skill 內的每一句指示都有不可替代的約束效力（例如 [[grill-me]] 僅用 5 行文字寫成）。

### 2. 指引詞（Signposts）
- **核心思想**：善用資訊被高度壓縮、在模型訓練資料中深植的專業領域經典術語，以極簡詞彙精準喚醒模型的先驗知識 ([[grill-me-matt-pocock]])。
- **實例**：
  - 與其花百字解釋「把總是綁定在一起的多個變數打包成物件」，不如直接指出避免 **Data Clumps**。
  - 借用 Martin Fowler《Refactoring》的經典術語（如 *Shotgun Surgery*、*Feature Envy*）作為 Code Review 的精確檢查清單。

### 3. 明確完成標準（Clear Completion Criteria）
- **核心思想**：給定清晰、具體且可驗證的結束條件，防止 AI 在任務中無限發散或過早交差 ([[grill-me-matt-pocock]])。

## 五大技能分類體系

在 `mattpocock/skills` 中，技能被有組織地劃分為五大模組，各自擔綱不同的工程職責 ([[mattpocock-skills-repo]])：
1. **需求分析與規劃**（如 `grill-me`、`grill-with-docs`、`to-spec`、`to-tickets`）：釐清盲點，產出不含 code 的規格與垂直功能任務。
2. **[[TDD|測試驅動開發 (TDD)]]**（如 `tdd`、`implement`、`implement-spec`）：以紅燈-綠燈-重構循環引導實作，杜絕 AI 偽造假測試。
3. **除錯與代碼審查**（如 `diagnosing-bugs`、`code-review`）：先重現問題、縮小範圍，以證據驅動除錯；審查品質與壞味道。
4. **架構改善**（如 `domain-modeling`、`codebase-design`、`improve-codebase-architecture`）：領域概念建模、改善模組邊界、維持[[深模組與淺模組|深模組架構]]。
5. **專案管理與協調**（如 `ask-matt`、`triage`、`retro`、`research`）：指派工作流、Issue 分流與復盤改善。

## 導入與實踐原則

- **與靜態專案規則互補**：Skill（如 `SKILL.md`）應專注於特定任務的操作流程，並與專案全域背景設定（如 `CLAUDE.md`）分工協作，參見 [[專案規則與技能工作流]] ([[mattpocock-skills-repo]])。
- **漸進式引入策略**：避免一開始將所有 Skill 全數掛載；應先引入需求分析、[[TDD]]、除錯與架構改善等核心模組，觀察效果後再逐步擴展 ([[mattpocock-skills-repo]])。

## 相關概念
- [[Matt Pocock]]
- [[Claude Code]]
- [[grill-me]]
- [[深模組與淺模組]]
- [[專案規則與技能工作流]]
- [[TDD]]
