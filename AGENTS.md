# LLM Wiki — Schema

這是一個依照 Karpathy「LLM Wiki」模式運作的個人知識庫（同時也是 Obsidian vault）。
你（LLM）是這個 wiki 的維護者：負責撰寫與維護 `wiki/` 內所有頁面；使用者負責挑選來源、引導方向與提問。
模式原文見 `raw/karpathy-llm-wiki-gist.md`。

本檔是 schema，隨使用經驗與使用者共同演進。調整慣例時先更新本檔，再套用到 wiki。

## 三層架構

| 層 | 位置 | 擁有者 | 規則 |
|---|---|---|---|
| Raw sources | `raw/` | 使用者 | **不可變**。只讀，絕不修改、改名或刪除。圖片附件在 `raw/assets/` |
| Wiki | `wiki/` | LLM | LLM 全權建立與維護；使用者只閱讀 |
| Schema | `AGENTS.md` | 共同 | 定義結構、慣例與工作流程 |

## 目錄結構

```
raw/                  原始來源（文章、論文、逐字稿、資料檔）
  assets/             來源的圖片附件（Obsidian 附件資料夾）
wiki/
  index.md            內容目錄：所有頁面的連結與一行摘要
  log.md              時間序紀錄：append-only
  overview.md         整體綜述：目前的全局理解與待解問題
  sources/            來源摘要頁，一個來源一頁
  entities/           實體頁：人物、組織、產品、工具、專案、地點
  concepts/           概念頁：想法、方法、理論、模式、主題
  analyses/           分析頁：由提問產生的比較、綜合、深入探討
```

## 頁面慣例

- **語言**：繁體中文撰寫；專有名詞保留原文（例：RAG、Obsidian、Memex）。
- **檔名**：
  - `sources/`：小寫 kebab-case，盡量對應 raw 檔名（`raw/foo-bar.md` → `wiki/sources/foo-bar.md`）。
  - `entities/`、`concepts/`：以該事物最通用的名稱命名，專有名詞用原文（`Andrej Karpathy.md`、`RAG.md`、`知識複利.md`）。
  - `analyses/`：簡短描述性標題（`RAG 與 LLM Wiki 比較.md`）。
  - 檔名在整個 wiki 中必須唯一，避免 `\ / : * ? " < > |`。
- **連結**：頁面之間一律使用 Obsidian wikilink `[[頁面名稱]]`（需要時 `[[頁面名稱|顯示文字]]`）。首次提及有專屬頁面的實體或概念時就加上連結。
- **引用**：每項事實性陳述都要能追溯到來源，在句末或段末標註 `([[來源頁名稱]])`。引用 raw 檔內的特定位置時可寫明章節或留言編號。
- **矛盾**：新來源與既有內容衝突時，不要默默覆寫。在相關頁面以 `> [!warning] 矛盾` callout 並列兩種說法與各自來源，並在 `overview.md` 的待解問題中記錄。
- **不確定**：推論或未經來源證實的內容以 `> [!question]` 標示，不可寫成事實。
- **寧少勿濫**：只有在某個實體或概念有足夠內容，或被兩個以上來源提及時才建立專屬頁面；否則先在相關頁面中描述。

### Frontmatter

每個 wiki 頁面（`index.md`、`log.md` 除外）開頭都有 YAML frontmatter：

```yaml
---
type: source | entity | concept | analysis | overview
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []        # 本頁依據的來源頁名稱；source 頁本身省略此欄
---
```

`source` 頁另加：

```yaml
raw: raw/檔名.md
author:
published: YYYY-MM-DD
url:
```

### 各類頁面的骨架

- **source**：一句話摘要 → 重點 → 值得注意的細節或數據 → 圖片觀察（選用；來源有圖片時，逐張記錄所見，讀圖得到的數值標明為估計）→ 與既有 wiki 的關係（支持、補充、矛盾）→ 提及的實體與概念（連結）。
- **entity**：是誰或是什麼（一段）→ 重要事實 → 與其他實體、概念的關係 → 各來源怎麼說。
- **concept**：定義（一段）→ 運作方式或要點 → 不同觀點與爭議 → 相關概念 → 待解問題。
- **analysis**：提出的問題 → 結論 → 推論過程與證據 → 限制與後續可查方向。

## 工作流程

### Ingest（匯入來源）

使用者把來源放進 `raw/` 並要求處理時，一次處理一個來源：

1. 完整閱讀來源。若引用了 `raw/assets/` 的圖片，讀完文字後再個別查看相關圖片。
2. 向使用者報告重點，並討論要強調什麼（使用者說要直接處理或批次匯入時略過討論）。
3. 在 `wiki/sources/` 建立摘要頁。
4. 更新或建立相關的 `entities/`、`concepts/` 頁面：補充新資訊、加上交叉連結、標示矛盾。
5. 視需要修訂 `overview.md`。
6. 更新 `index.md`。
7. 在 `log.md` 附加一筆紀錄，列出新增與修改的頁面。

超大型來源（例如含上千則留言的討論串）分段閱讀，先處理主體，再依使用者指示決定次要部分要處理到多深。

### Query（提問）

1. 先讀 `index.md` 找出相關頁面，再讀這些頁面；wiki 內容不足時才回頭查 `raw/`。
2. 綜合回答並附上引用（連到 wiki 頁面）。清楚區分「wiki 有記載」與「自己的推論」。
3. 答案若有長期價值（比較、分析、新發現的關聯），詢問使用者是否歸檔到 `analyses/`；歸檔後更新 `index.md` 並記錄到 `log.md`。
4. 提問過程中發現 wiki 的缺口或錯誤，順手修正或提出來。

### Lint（健檢）

使用者要求健檢時檢查並回報，取得同意後修正：

- 頁面之間的矛盾、被新來源取代的過時陳述
- 沒有任何頁面連入的孤兒頁面、指向不存在頁面的連結
- 多次被提及卻沒有專屬頁面的重要實體或概念
- 缺少的交叉連結、缺少引用的陳述
- `index.md` 與實際檔案不一致、frontmatter 缺漏
- 值得進一步調查的問題、值得尋找的新來源

## index.md 與 log.md

- **`index.md`**：依類別（總覽、來源、實體、概念、分析）列出所有頁面，每項格式為 `- [[頁面名稱]] — 一行摘要`。每次新增、改名或刪除頁面都要同步更新。
- **`log.md`**：只能在檔尾附加，不修改既有紀錄。每筆以固定前綴開頭，方便用工具解析：

  ```
  ## [YYYY-MM-DD] ingest | 來源標題
  ## [YYYY-MM-DD] query | 問題摘要
  ## [YYYY-MM-DD] lint | 範圍
  ## [YYYY-MM-DD] schema | 變更摘要
  ```

  標題下方用條列簡述做了什麼、動到哪些頁面。查看最近紀錄：`grep "^## \[" wiki/log.md | tail -5`

## 每次工作開始時

先讀 `wiki/index.md` 與 `wiki/log.md` 的最後幾筆紀錄，掌握 wiki 目前的狀態再動手。
