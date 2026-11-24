---
name: handoff
description: 把目前的進度寫成一段 prompt，貼到新的 session 就能接著做下一階段。當使用者說「交接」、「開新 session 接著做」時觸發。
---

# Handoff：把下一階段交給新的 session

目前的 session 完成了一個階段，使用者要開新的 session。產出一段 prompt，貼到新的 session 就能馬上開始下一階段的工作。

## 流程

1. 從對話看不出下一階段是什麼時，只問一個問題：「下一個 session 要做什麼？」
2. 跑 `git status`，確認還沒 commit 與還沒 push 的變更
3. 照下面的結構起草，整份不超過 15 行
4. 逐行檢查：每一行都要說得出它讓新的 session 避開哪件事，例如做錯、重做、重新討論已定案的事
5. 印出 prompt，前後不加任何說明文字

## 結構

- 任務：一句話寫下一階段要做什麼，以及第一個動作
- 決定：這個 session 定案、新的 session 可能重新討論的事，每項一行，寫選了什麼。只寫下一階段會碰到的
- 做法：這個 session 定下、看 commit 也看不出來的步驟，例如怎麼驗證、要順便處理什麼
- 先看：檔案路徑或 commit，不摘要它們的內容
- 狀態：新的 session 跑 `git status` 也看不出意圖的事，例如還沒 push 的 commit、執行中的伺服器、不屬於這個任務的未追蹤檔案

沒有內容的項目整個省略。新的 session 會載入一樣的 `CLAUDE.md`、skill、codebase 與 git 記錄，裡面已經有的不寫；跟下一階段無關的待辦也不寫。
