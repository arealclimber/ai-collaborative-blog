---
title: "Commitizen"
date: 2024-09-15T20:00:44+08:00
draft: true # 隱藏 AI 工具文章
author: "Shirley"
tags: [""]
---

# 為什麼要使用 Git Commit Message Tool

- 團隊開發時，清晰的提交訊息 (commit message) ，可以讓自己跟其他工程師一眼就明白該 commit 做的事情，也方便之後系統出現問題時，可以更快速的排查問題跟回溯。
- 常見的 commit 有以下幾種類型：
  1. feat: 新功能
  2. fix: 錯誤修復
  3. docs: 文檔更新
  4. style: 代碼格式修改,不影響代碼邏輯
  5. refactor: 代碼重構,既不修復錯誤也不添加功能
  6. perf: 性能優化
  7. test: 添加或修改測試用例
  8. chore: 構建過程或輔助工具的變動
- 透過提交訊息工具，讓開發者減少統一提交訊息的負擔，不需特別記有哪些訊息種類

# 什麼是 [commitizen](https://commitizen.github.io/cz-cli/)

[Commitizen](https://commitizen.github.io/cz-cli/) 是一個互動式的 commit message 輔助工具，透過選單引導使用者填寫符合規範的 commit message。

commitizen 是基於 Node.js 撰寫的，需要在 Node.js 環境中運行。這使得 commitizen 能夠與 npm 和其他 JavaScript 工具無縫集成。

# 如何在 Javascript / Typescript 專案導入 commitizen

```bash
git init

npm init

npm install -D commitizen cz-conventional-changelog

```

- 新增 `.gitignore`，將 `node_modules/` 放進 `.gitignore`
- 修改 package.json
  ```json
  {
  ...
    "scripts": {
  ...
      "commit": "cz"
    },
  ...
    "config": {
      "commitizen": {
        "path": "./node_modules/cz-conventional-changelog"
      }
    }
  }

  ```
- 新增一個 commit 作為測試
  1. `git add .`
  2. `npm run commit`
     1. 接下來依序填寫每個選項
     2. 新增 issues 作為 reference ，如果寫上 `fix #<ISSUE_NUMBER>` 就會在 commit 被合併到 main branch 時，自動關閉該 issue；如果只是單純標注 `#<ISSUE_NUMBER>`，則只會讓該 issue 顯示 commit 連結，不會關閉

        ```json
        ? Select the type of change that you're committing: feat:
        A new feature

        ? What is the scope of this change (e.g. component or file
        name): (press enter to skip)

        ? Write a short, imperative tense description of the change
        (max 94 chars):
         (4) test

        ? Provide a longer description of the change: (press enter to
        skip)

        ? Are there any breaking changes? No

        ? Does this change affect any open issues? Yes

        ? If issues are closed, the commit requires a body. Please
        enter a longer description of the commit itself:
         -

        ? Add issue references (e.g. "fix #123", "re #123".):
         fix #1

        ```

### 將 commitizen 產生的 changelog.md 作為 release 內容

需要安裝 `standard-version`

```bash
npm install --save-dev standard-version

```

- 修改 package.json
  ```bash
  {
    "scripts": {
  ...
      "release": "standard-version"
    },
  }

  ```
- `npm run release`
- `git push --follow-tags origin main && npm publish`
  - 會更新 CHANGELOG.md
  - 可以同步 release 到 npm 跟 GitHub 上；如果沒有登入 npm，一樣可以成功在 GitHub 遠端看到 release

# 如何在全域下使用 commitizen

- 根據不同作業系統，透過 [nvm](https://github.com/nvm-sh/nvm) 下載跟管理 Node.js 跟 npm
- 全域安裝

```json
npm install -g commitizen cz-conventional-changelog

```

- 在專案下執行以下指令，則可使用 commitizen
  ```bash
  git add .
  git cz commit

  ```
