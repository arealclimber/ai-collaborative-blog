# Initialization

## 安裝 hugo

- 根據不同作業系統安裝 hugo，參考[官方文件](https://gohugo.io/installation/)
- 確保 hugo 安裝成功，可輸入指令查看版本
  - `hugo version`

## clone repo

- `git clone https://github.com/arealclimber/ai-collaborative-blog.git`
- `cd ai-collaborative-blog`

# 新增文章

- 流程為：寫文章 →build 整個 repo 的靜態文件 → 將更新推到遠端 → 查看 GitHub 自動部署是否成功、網站是否將新文章更新上來

## 寫文章

- 創建文章：`hugo new <DIR/FILE_NAME.md>`
  - 範例：`hugo new posts/test-article.md`
- 執行完指令，`test-article.md` 會得到以下內容

  ```tsx
  +++
  title: 'Test Article'
  date: 2024-06-23T20:49:50+08:00
  draft: true
  author: ''
  +++

  ```

- 將預設值的 `+++` 更改為 `---`、在作者欄加上自己的名字、在文章完成後將 drafe 改為 false：

```tsx
---
title: 'Test Article'
date: 2024-06-23T20:49:50+08:00
draft: true
author: "作者名字"
---

開始寫文章....
```

## build 靜態文件

- build 靜態文件
  - `hugo`
- 在本地跑 hugo server 查看動態變化
  - `hugo server`

## 將更新推到遠端

- `git add .`
- `git commit -m "YOUR_COMMIT_MESSAGE”`

### 查看 GitHub 自動部署是否成功、網站是否將新文章更新上來

- [查看自動部署紀錄](https://github.com/arealclimber/ai-collaborative-blog/deployments/Production)
- [查看網站](https://ai-co-blog.vercel.app/)

## 注意事項

- 如果 server 跑起來沒看到文章，可能是日期超過當下的時間
