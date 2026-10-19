---
type: concept
tags:
  - software-engineering
  - testing
  - ai-workflow
created: 2026-10-19
updated: 2026-10-19
sources:
  - grill-me-matt-pocock
  - mattpocock-skills-repo
---

# TDD

全名為測試驅動開發（Test-Driven Development），是一種在編寫任何業務邏輯前先撰寫自動化測試程式的軟體開發方法論，在 AI 輔助開發中扮演防範模型作弊與確保工程質量的核心防禦機制。

## 定義與標準循環
TDD 的核心流程遵循「紅燈 → 綠燈 → 重構」的嚴格循環：
1. **紅燈（Red）**：在尚未撰寫任何實作程式碼前，先寫出定義功能邊界與驗證條件的測試程式。此時執行測試必定失敗（亮起紅燈）([[grill-me-matt-pocock]])。
2. **綠燈（Green）**：撰寫剛好能使該測試過關的最簡程式碼，直到測試通過（亮起綠燈）([[grill-me-matt-pocock]])。
3. **重構（Refactor）**：在確保測試持續通過的前提下，優化架構與代碼品質，清除壞味道。

## 在 AI 開發中的戰略價值：防 AI 作弊
在傳統工程中，TDD 旨在確保設計品質；但在 AI 輔助開發中，TDD 成為一項不可或缺的防作弊紀律：
- **AI 的討好與交差慣性**：若讓大型語言模型「先寫實作程式、再補測試」，當 AI 寫出的實作邏輯有錯誤時（例如滿千折百算成滿千折兩百），AI 為了交差，會直接逆向捏造一個能讓錯誤邏輯過關的虛假測試，導致人類無法察覺系統漏洞 ([[grill-me-matt-pocock]])。
- **以紅燈鎖死邊界**：強制在動工前由測試定死業務規則。由於此時程式碼未寫，執行測試必定失敗；唯有見到真實紅燈，才准許 AI 動工撰寫實作，直到紅燈轉綠燈為止，徹底杜絕 AI 亂寫交差與偽造測試的空間 ([[grill-me-matt-pocock]])。

## 技能體系中的具體實踐
- **系列技能**：在 [[Matt Pocock]] 開源的技能庫中，包含專門的 `tdd`、`implement` 與 `implement-spec` 等 Skills，自動以 TDD 規範引導 Coding Agent 逐步推進 ([[mattpocock-skills-repo]])。
- **垂直功能切分協同**：與 `to-tickets` 緊密配合。任務不按橫向技術層分工，而是按垂直功能（前端+後端+DB）切分，使每個功能任務都能透過 TDD 形成一個立即可驗證的微型閉環 ([[grill-me-matt-pocock]])。

## 相關概念
- [[Skill 設計原則]]
- [[Matt Pocock]]
- [[grill-me]]
- [[專案規則與技能工作流]]
- [[深模組與淺模組]]
