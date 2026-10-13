# Conventional Commits 格式

```
<type>(<scope>): <short summary>
```

- `type`：feat、fix、docs、style、refactor、perf、test、build、ci、chore、revert 之一
- `scope`：可省略，沿用 `git log --oneline -- <files>` 裡已有的名稱
- 摘要：冒號後小寫

範例：`fix(auth): handle expired token refresh`
