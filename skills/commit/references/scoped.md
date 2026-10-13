# Scoped 格式

Linux、Git、Go 的風格，不帶 type 標籤。

```
<scope>: <short summary>
```

- `scope`：變更所在的子系統、套件路徑或目錄，沿用 `git log --oneline -- <files>` 裡已有的名稱
- 摘要：冒號後小寫

範例：`auth: handle expired token refresh`
