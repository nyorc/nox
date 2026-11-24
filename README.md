# nox

我自己日常使用的 agent skills

## 安裝

Claude code
```bash
claude plugin install nox --marketplace nyorc/nox
```

## Skills

- `commit`：依 repo 既有 commit 風格 commit
- `scoped-commit`：同一套流程，風格固定為 `scope: description`（Linux/Git/Go 風格）
- `conventional-commit`：同一套流程，風格固定為 `type(scope): description`（Conventional Commits）
- `debugging`：系統化追出錯誤的根本原因，再動手修正
- `tdd`：用紅燈、綠燈、重構的循環與 Tidy First 做測試驅動開發
- `next`：依目前的對話提出接下來可以做的事，並建議先做哪一項，只提議不動手
- `handoff`：把目前的進度寫成一段 prompt，貼到新的 session 就能接著做下一階段
- `sketch-it`：把對話或檔案裡一段長文字畫成一張 ASCII 圖

## 授權

[MIT](LICENSE)
