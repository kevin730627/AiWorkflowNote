---
title: "介紹 Skills 專案"
source: "https://chatgpt.com/c/6ad5afec-5c04-83ee-819f-7fa10f3ffb7c"
author:
published: 2026-10-18
created: 2026-10-19
description:
tags:
  - "clippings"
---
To pick up a draggable item, press the space bar. While dragging, use the arrow keys to move the item. Press space again to drop the item in its new position, or press escape to cancel.

[https://github.com/mattpocock/skills](https://github.com/mattpocock/skills)  
這裡面是什麼?

這個 GitHub 專案 [mattpocock/skills](https://github.com/mattpocock/skills?utm_source=chatgpt.com) 是 TypeScript 開發者 Matt Pocock 整理的一套 AI 程式開發 Skills（技能指令集），目的是讓 Claude Code、Codex 等 AI 程式代理，在開發軟體時遵循更有紀律、可重複的工程流程，而不是只根據一句 Prompt 就直接開始寫程式。

skills.rest

+1

你可以把它理解成：替 AI 程式助手安裝一套資深工程師的工作方法。

它不是一個獨立的 AI 模型，也不是需要啟動的應用程式。主要內容是 `SKILL.md` 等 Markdown 指令文件，告訴 AI 在特定情境下應該如何思考、規劃、測試和修改程式碼。

## 一、裡面有哪些 Skills？

以下是這個專案的主要技能類型與用途。

Skills Docs

+1

1\. 需求分析與規劃

`grill-me` 、 `grill-with-docs` 、 `to-spec` 、 `to-tickets`

- 在寫程式前，先透過提問釐清需求。
- 找出尚未決定的設計細節與例外情況。
- 將想法整理成規格文件（Spec）及可執行的開發任務（Tickets）。

2\. 測試驅動開發（TDD）

`tdd` 、 `implement` 、 `implement-spec`

- 先建立測試，再實作功能。
- 以測試失敗、測試通過、重構的循環逐步開發。
- 依照規格逐項實作，而不是一次生成大量程式碼。

3\. 除錯與程式碼審查

`diagnosing-bugs` 、 `code-review`

- 先重現 Bug，再縮小問題範圍。
- 根據假設收集證據，避免盲目修改。
- 檢查程式碼品質、規格符合度及可能的回歸問題。

4\. 架構與程式碼改善

`domain-modeling` 、 `codebase-design` 、 `improve-codebase-architecture`

- 整理專案中的核心概念與術語。
- 改善模組邊界及介面設計。
- 找出架構逐漸混亂、難以維護的地方。

5\. 專案管理與工作流程

`ask-matt` 、 `triage` 、 `retro` 、 `research`

- 依照問題選擇適合的 Skill 或開發流程。
- 分類與安排 Bug、需求及待辦工作。
- 回顧開發過程，改善測試、文件及專案規則。

## 二、它跟一般的 CLAUDE.md 有什麼不同？

| 比較項目 | `CLAUDE.md` | Matt Pocock Skills |
| --- | --- | --- |
| 主要用途 | 專案的長期規則與背景 | 特定工作的操作流程 |
| 內容 | 專案架構、命名規則、限制 | 規劃、測試、除錯、審查步驟 |
| 何時使用 | Claude Code 讀取專案指引時 | 依照呼叫方式及 Skill 的設定觸發 |
| 能否客製化 | 可以 | 可以 |
| 能否搭配使用 | 可以 | 可以 |

例如，你可以在 `CLAUDE.md` 裡規定：

> 開發 Blender Addon 時，必須支援 Blender 4.5～5.2，並遵循既有架構。

再搭配 `tdd` Skill，要求 AI 先寫測試、驗證功能，再進行重構。

兩者是互補關係，不需要二選一。

## 三、怎麼安裝？

專案提供 Skills CLI 安裝方式，也支援 Claude Code 的 Plugin 安裝途徑。

ScratchDB

+1

如果你主要使用 Claude Code，可以先進入專案資料夾，執行：

Bash

```
npx skills@latest add mattpocock/skills
```

依照安裝器的提示選擇需要的 Skills 和 AI 工具，再執行：

純文字

`/setup-matt-pocock-skills`

這個初始化流程會詢問你使用哪種 Issue Tracker（例如 GitHub、Linear 或本機檔案），以及任務分類標籤等設定。

注意：這是會修改 AI 開發環境的第三方指令集，建議先閱讀要安裝的 Skill 文件，再授予必要的檔案或外部服務權限。

## 四、適不適合你目前的 Blender Addon 專案？

我認為很值得嘗試，尤其是你正在開發的 Blender 3D 列印切片、模型修復及挖空 Addon。

優先使用： `grill-me` / `grill-with-docs`

在實作前釐清模型修復、挖空、排水孔與切片的需求，降低 AI 自行猜測規格的機率。

優先使用： `tdd`

為網格處理、幾何運算、檔案匯入及參數驗證建立測試，減少修改一項功能卻破壞其他功能的情況。

優先使用： `diagnosing-bugs`

當 Blender Python API、網格布林運算或切片結果出錯時，要求 AI 先重現問題、定位原因，再修正並加入回歸測試。

優先使用： `improve-codebase-architecture`

當 Addon 越來越大時，檢查 UI、幾何演算法、切片器介接與資料管理之間的耦合問題。

以上是依照各 Skill 的用途提出的建議，不代表它們已經針對 Blender API 或你的 Addon 做過專門驗證。

我的建議： 不要一開始就把所有 Skills 都安裝進去。先選需求分析、TDD、除錯及架構改善這幾類，觀察它們是否真的改善 Claude Code 的開發品質，再逐步增加。

你可以從原始專案的 [README 與完整 Skills 清單](https://github.com/mattpocock/skills?utm_source=chatgpt.com) 開始查看。

ChatGPT 可能會出錯。請查證重要資訊。

To pick up a draggable item, press the space bar. While dragging, use the arrow keys to move the item. Press space again to drop the item in its new position, or press escape to cancel.

<iframe sandbox="allow-scripts" src="https://cdn.platform.openai.com/deployments/dil/v14/runner.html" title="DIL execution sandbox"></iframe>

To pick up a draggable item, press the space bar. While dragging, use the arrow keys to move the item. Press space again to drop the item in its new position, or press escape to cancel.