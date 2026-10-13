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
