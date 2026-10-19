---
type: source
tags:
  - ai-workflow
  - prompt-engineering
  - software-engineering
created: 2026-10-19
updated: 2026-10-19
raw: raw/(3011) 700 萬人下載的 grill-me，Matt Pocock 到底寫了什麼？.md
author: Matt Pocock 工作流解析者
published: 2026-10-18
url: https://www.youtube.com/watch?v=aR97E7aKEgg
---

# (3011) 700 萬人下載的 grill-me，Matt Pocock 到底寫了什麼？

## 一句話摘要
解析 TypeScript 專家 [[Matt Pocock]] 所開源的高人氣 AI 開發 Skill 工具集，探討其如何透過極簡模組化設計、反向拷問機制、[[TDD]] 防作弊與深模組架構，將軟體工程實踐融入提示詞來有效駕馭 AI。

## 重點
- **Vibe Coding 的風險與控制隨機性**：隨意將模糊想法交由 AI 開發等於將數百個微觀決策外包，AI 往往寫出難以維護的架構。開發的核心挑戰是控制 AI 的隨機性。
- **五大核心 Skill 鏈結**：
  1. `/grill-me`：僅 5 行 Prompt，讓 AI 順著決策樹無情拷問人類盲點，一次一題且附帶建議，未達成共識前嚴格禁止動工寫 code。
  2. `/to-spec`：將討論共識凝結為規格書，嚴格禁止寫入具體程式碼，以避免日後規格與實作脫節，過期 code 混淆 AI。
  3. `/to-tickets`：強制按「使用者可見功能」垂直切分任務（包含完整 DB、邏輯、畫面），而非按技術分工，確保每一步皆能立即由人類驗證。
  4. `/implement` 與 [[TDD]]：先寫測試至紅燈，再寫程式轉綠燈，徹底鎖死 AI 偽造測試以交差的作弊空間。
  5. `Code Review`：啟動獨立乾淨的 session，以《Refactoring》經典壞味道（如 *Shotgun Surgery*、*Feature Envy*、*Data Clumps*）作為具體檢查依據。
- **[[Skill 設計原則]]（`writing-great-skills`）**：
  - **Pruning（修剪）**：刪除冗言贅字與模型已知的多餘指示。
  - **Signposts（指引詞）**：使用資訊高度壓縮的領域專業術語精準喚起模型先驗知識。
  - **Completion Criteria（明確完成標準）**：給定清晰收尾條件。
- **[[深模組與淺模組]]的架構治理**：AI 因 Context Window 有限容易寫出「淺模組」，導致跨檔迷路；應追求介面極簡、邏輯封裝的「深模組」，並透過 `improve-codebase-architecture` 的刪除測試定期重構。
- **對比 [[Superpowers]]**：Superpowers 採 9 步驟寫死重型固定流程，適合弱模型防呆；Matt Pocock 的工具組採極簡模組化樂高積木，更能發揮現代高智能模型的威力。

## 值得注意的細節或數據
- 專案在 GitHub 上獲得超過 16 萬顆星，下載量達 700 萬次。
- `/grill-me` 原始碼僅有 5 行文字，包含四大要求：未達共識前拷問到底、順著決策樹延伸、每次只問一題附建議、達成共識前禁止寫程式。
- `/grill-with-docs` 為進化版，拷問過程中會記錄專案名詞定義與決策文件，避免新對話重新摸索背景。
- Code Review skill 內建了 12 種出自 Martin Fowler《Refactoring》的壞代碼症狀檢查。

## 與既有 wiki 的關係
- 本篇為知識庫匯入的第一篇來源，奠定了 AI 輔助軟體開發工作流的基準架構概念。

## 提及的實體與概念
- 實體：[[Matt Pocock]]、[[Superpowers]]
- 概念：[[grill-me]]、[[深模組與淺模組]]、[[Skill 設計原則]]、[[TDD]]
