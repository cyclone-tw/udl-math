# 數學練習室（udl-math）

數學互動練習的集中庫。入口網站用卡片列出每一個練習：適合誰、在學什麼、縮圖，點卡片就進入該練習。

線上入口：<https://cyclone-tw.github.io/udl-math/>

## 在 UDL 教學家族的位置

本 repo 是 UDL 教學家族的數學教材 repo，家族裡的數學都集中在這裡。2026-10-14 以前叫 `cyclone-math-lab`；舊網址 `cyclone-tw.github.io/cyclone-math-lab/` 已不再提供，請改用上面的新網址。

- 題型、數學出題規則、作答紀錄格式照公開規格 [`udl-content-spec`](https://github.com/cyclone-tw/udl-content-spec)。
- 之後會掛進 `udl-learning` 的 RPG 教學平台，由平台負責登入、分配與作答紀錄；改寫時間等平台畫面架構定案。
- 給 agent 的規則與家族地圖入口見 [`AGENTS.md`](AGENTS.md)。

## 目錄

- `site/`：入口網站與 `catalog.json`
- `site/thumbs/`：卡片縮圖
- `activities/<slug>/`：各練習原始碼
- `scripts/build-site.mjs`：把入口和練習編成 `docs/`

`catalog.json` 的 `kind`：

- `vite`：該資料夾是 Vite 專案，建置時會跑 `pnpm run build`
- `static`：該資料夾已是可直接打開的 HTML，建置時整包複製

## 本機

```bash
pnpm run dev
pnpm run site
```

`pnpm run site` 會產生 `docs/`。入口在 `docs/index.html`，練習在 `docs/play/<slug>/`。

## 新增一個練習

1. 靜態 HTML 放進 `activities/<slug>/index.html`；需要建置的專案放進 `activities/<slug>/` 並在 `package.json` 提供 `build`。
2. 縮圖放到 `site/thumbs/<slug>.png`（建議橫向，約 16:10）。
3. 在 `site/catalog.json` 加一筆：`title`、`audience`、`learns`、`summary`、`tags`、`thumb`、`href`、`kind`、`source`。
4. 推上 `main` 後，Pages 會重新發布。
