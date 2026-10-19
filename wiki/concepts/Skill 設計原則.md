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
---

# Skill 設計原則

[[Matt Pocock]] 在其開源專案中的 `writing-great-skills` 所歸納出用以撰寫高效 AI Agent Skill / Prompt 的三大核心原則。

## 三大核心原則

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

## 相關概念
- [[Matt Pocock]]
- [[grill-me]]
- [[深模組與淺模組]]
