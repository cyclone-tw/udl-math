# AGENTS.md — udl-math

所有 coding agent 進本 repo 先讀這份。全域規則（cyclone-agent-config）照常適用，此處只列本 repo 特有規則。

<!-- udl-family-block v1 -->
> **UDL 教學家族**：本 repo 是數學教材 repo（數學練習室），家族裡的數學都集中在這裡；2026-10-14 前叫 `cyclone-math-lab`。
>
> 上游：`udl-content-spec`（題型、數學參數化產生器、作答事件格式）、`sped-student-kit`（能力階梯）；下游：`udl-learning` 的 RPG 平台（之後以內容包或活動掛進去呈現）。
>
> 家族地圖正本：`cyclone-tw/udl-learning` 的 `docs/family-map.md`（私人 repo）。要改本 repo 的角色或串接方式，先改地圖。
<!-- /udl-family-block -->

## 現況與方向

- 現在：公開 repo＋GitHub Pages 入口 <https://cyclone-tw.github.io/udl-math/>，卡片資料在 `site/catalog.json`，各練習在 `activities/<slug>/`（建置方式見 `README.md`）。
- 方向（Cyclone 2026-10-14）：數學教材集中在本 repo；**整體改寫等 udl-learning 的 RPG 平台 UI/UX 架構定案後再做**。改寫時：
  - 練習改成照 `udl-content-spec` 的內容包，或實作「自帶畫面的活動」契約（`mount()`＋作答事件），掛進平台呈現（udl-learning 總規劃 §4.4）。
  - 本 repo 轉私人，由平台登入後提供（udl-learning `AGENTS.md` 硬紅線 5：程式碼與素材不讓人整包端走）。
  - 舊的 `math-vertical`、`math-shooter`、`math-meteor-shooter`、`edu-math` 值得留的併進來，其餘封存。
- 在那之前：可以照現有方式修錯或加練習，但不要自建登入、帳號、紀錄後端或教師端；這些都歸平台。

## 硬紅線

1. 這是公開 repo：有價值的題庫、出題工具或素材要放進來之前，先問 Cyclone（udl-learning `AGENTS.md` 硬紅線 5）。
2. Secrets／token／`.env` 不進 git。
3. 圖內不要文字、字母、數字、浮水印（美術方向照 udl-learning `docs/art-direction.md`）。

## 開發流程

- Issue-first；branch → PR → 受管跨 agent review（`openab-review`）→ approved 或 nits-only＋CI 綠就 merge；Coder ≠ Reviewer。
- 共用 checkout 不切分支；在 `~/Cyclone-System/worktrees/udl-math-<issue>-<slug>` 開自己的 worktree。
- 書商教材（教師資源、考卷）固定放學校 Drive `04.學校相關/02.特教教學/03.教材資源/`：要找先讀 `03.教材編輯/README-教材索引.md`，新檔用 udl-learning 的 `scripts/intake_teaching_material.py` 收件（規則見 udl-learning `docs/authoring/publisher-materials.md`，udl-learning#446）。書商原始檔有版權，不進本公開 repo。
- 一律 pnpm。推上 `main` 後由 `.github/workflows/pages.yml` 建置並發布 Pages。
- 作答介面照家族慣例：觸控優先、目標 48px 以上、答錯不羞辱、支援 `prefers-reduced-motion`。
