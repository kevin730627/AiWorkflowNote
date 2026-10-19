---
type: entity
tags:
  - tool
  - ai-agent
  - anthropic
  - cli
created: 2026-10-19
updated: 2026-10-19
sources:
  - mattpocock-skills-repo
---

# Claude Code

Anthropic 開發的官方終端機命令行 AI 軟體工程代理（Coding Agent），能在本地環境中直接執行指令、讀寫檔案、執行測試並協同開發。

## 重要事實
- **宿主與執行環境**：作為執行 AI Skills（如 `mattpocock/skills`）的主要終端機 Agent 宿主之一 ([[mattpocock-skills-repo]])。
- **指引載體**：透過專案根目錄的 `CLAUDE.md` 讀取專案的長期架構規則與約束，並透過 Skill 系統（如 `SKILL.md`）掛載特定任務的動態工作流程 ([[mattpocock-skills-repo]])。
- **外掛擴充性**：支援透過 NPM/CLI 工具（如 `npx skills`）或 Plugin 機制擴充技能集，讓 Agent 具備資深工程師的測試驅動、除錯與架構重構能力 ([[mattpocock-skills-repo]])。

## 與其他實體、概念的關係
- 為 [[Matt Pocock]] 的開源 Skills 專案提供執行環境。
- 實踐了 [[專案規則與技能工作流]] 中靜態規則與動態指令集的分工協作。

## 各來源怎麼說
- [[mattpocock-skills-repo]] 說明 Claude Code 藉由掛載模組化 Skills，能擺脫單純依靠單次 Prompt 寫程式的隨機性，轉而遵循嚴謹可重複的工程規範。
