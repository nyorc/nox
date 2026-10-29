---
name: commit
description: 依照 repo 既有的 commit 風格進行 commit。當使用者要求建立 git commit 時觸發。
---

# Commit

提交 repo 變動，訊息沿用 repo 既有的風格。

## 流程

1. 平行執行三個指令收集資訊：
   - `git status`
   - `git diff HEAD`
   - `git log --no-merges -n 3 --format=%s`

   沒有變更就停下來告訴使用者，不建立空 commit。

2. 依「選擇風格」決定風格，再讀對應檔案取得格式規則：
   - `references/conventional.md`：`type(scope): summary`
   - `references/scoped.md`：`scope: summary`
   - `references/plain.md`：主旨開頭不帶 `xxx:`

   用一行 `style: <風格> (<依據>)` 回報，讓使用者有機會改口。依各條規則的範例：

   ```
   style: scoped (fixed by /nox:scoped-commit)    # 規則 1
   style: conventional (CONTRIBUTING.md)          # 規則 2
   style: scoped (from "parser: handle eof")      # 規則 3
   ```

3. 暫存（stage）：
   - 決定範圍：變更分屬多件事時只放最主要，分不出主要次要就提議拆成多個 commit，詢問使用者
   - 檢查機密：.env、憑證等檔案預設不暫存，並告訴使用者略過了哪些檔案
   - 加入：用 `git add <檔案>` 指名
   - 確認：讀 `git diff --cached`，暫存內容符合預期才往下走

4. 提交（commit）：
   - 預設只寫主旨（`git commit -m "<subject>"`）
   - 主旨用英文寫，不超過 72 個字元，用祈使句，結尾不加句號
   - 符合「訊息本文」的條件才加本文
   - 不加 Co-Authored-By

## 選擇風格

依序檢查，第一條有答案就停：

1. 已指定的風格。
2. `CLAUDE.md`、`CONTRIBUTING.md` 寫明的 commit 規則。
3. 最新一條主旨的風格：冒號前是 feat、fix 這類 type 為 Conventional，是其他詞為 Scoped，沒有冒號開頭為 Plain。
4. repo 還沒有任何 commit：Conventional。

## 訊息本文

主旨說不完這個 commit 帶來的結果時才加本文，用條列寫結果，不寫原因、背景或取捨理由：

- 每條是一個可觀察的結果，例如行為改變、預設值、錯誤處理方式
- 繞過上游 bug 的 workaround 附 issue 連結

用 HEREDOC 傳入：

```bash
git commit -m "$(cat <<'EOF'
parser: switch tokenizer to streaming mode

- Tokenize input as a stream instead of recursively
- Accept inputs over 50k tokens
EOF
)"
```
