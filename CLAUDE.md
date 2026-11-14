# NASA Hackathon 2026：org 標準 CLAUDE.md

GitHub org：<https://github.com/nasa-hackathon-2026>（Free 方案，Owner 為個人帳號 Grasonyang）。

本檔是 org 所有 repo 共用的標準，唯一來源是 `nasa-hackathon-2026/org-standards` 這個 repo。要改規則就改這裡並 commit，不要改本機根目錄的 `CLAUDE.md`。這個 repo 是 public，內容不可放帳密、token、API key 或個人資料。

## 目錄結構

- 本機根目錄 `~/Documents/Nasa-Hackathon-2026/` 不是 git repo，只是 org 的工作資料夾。
- 根目錄的 `CLAUDE.md` 只做一件事：用 `@org-standards/CLAUDE.md` 匯入本檔。因為 Claude Code 會從啟動目錄往上找 `CLAUDE.md`，所以在任何 repo 裡啟動都會載入本檔。
- 每個比賽 repo 都 clone 在根目錄底下，與 `org-standards` 平行。repo 自己的技術細節寫在該 repo 的 `CLAUDE.md`，不要重複本檔內容。
- 不另外建立 `AGENTS.md`。

## 開發流程：Matt Pocock skills

每個 repo 都照 Matt Pocock skills 的流程開發（路由總覽見 `/ask-matt`）。

1. **新 repo 先跑一次 `/setup-matt-pocock-skills`。** Issue tracker 用該 repo 的 GitHub Issues，triage labels 用預設值，domain docs 用 single-context。它會在 repo 的 `CLAUDE.md` 寫入 `## Agent skills` 區塊，並產生 `docs/agents/*.md`。
2. **主流程（想法到上線）：**
   - `/grill-with-docs`：用訪談釐清想法，結論累積在 repo 的 `CONTEXT.md` 與 `docs/adr/`。
   - 有問題必須靠可執行的東西才能回答時：`/handoff` 開新 session，用 `/prototype` 做拋棄式程式，再 `/handoff` 把結論帶回來。
   - 要跨多個 session 才做得完：`/to-spec` 再 `/to-tickets`（切成 tracer-bullet tickets，標明阻擋關係），之後每張 ticket 開乾淨的 context 跑 `/implement`。
   - 一個 session 做得完：直接 `/implement`。
   - `/implement` 內部用 `/tdd` 一個 red-green 切片一個切片做，結束前跑 `/code-review`（Standards + Spec 兩軸）才 commit。
3. **其他入口：**
   - 東西壞了、不好重現：`/diagnosing-bugs`。
   - 別人提的 bug 或需求：`/triage`（`/to-tickets` 產生的 ticket 已是 agent-ready，不用 triage）。
   - 一個 session 裝不下的模糊大目標：`/wayfinder`。
   - context 快滿：`/handoff`；`/to-tickets` 之前不要 compact 或 clear。

## Basic Memory 記錄

每個 repo 的重要進展都要持續記到 Basic Memory（project `main`）。

- **位置：** org 層級的事（成員、權限、整體決策、本檔的演變）放 `projects/Nasa-Hackathon-2026/`；各 repo 的筆記放 `projects/Nasa-Hackathon-2026/<repo 名>/`。
- **時機：** 做出有替代方案的決策（`/basic-memory:bm-decide`）、收工或交接前（`/basic-memory:bm-checkpoint`）、踩雷或環境設定（`/basic-memory:bm-remember`）。
- **格式：** 標題用繁體中文，tags 用英文 kebab-case，結尾放 `## 相關` 區塊並用 `[[標題]]` 連結。每個 repo 的筆記都要連回「NASA Hackathon 2026 GitHub org 初始化紀錄」。不寫帳密、token、API key。
- **分工，避免寫兩份：** `CONTEXT.md`、ADR、GitHub Issues 與 PR 是 repo 內的事實來源。Basic Memory 只放決策的指標、檢查點與踩雷，內容連到 ADR、issue 或 PR，不重複貼全文。

## 新增比賽 repo 的步驟

1. 在 org 建 repo，clone 到根目錄底下（與 `org-standards` 平行）。
2. 在 repo 裡啟動 Claude Code，跑 `/setup-matt-pocock-skills`。
3. 在 Basic Memory 建 `projects/Nasa-Hackathon-2026/<repo 名>/` 的第一篇筆記，連回 org 初始化紀錄。
