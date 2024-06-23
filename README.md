# 安裝 hugo 跟 clone repo

- 根據不同作業系統安裝 hugo，參考[官方文件](https://gohugo.io/installation/)
- 確保 hugo 安裝成功，可輸入指令查看版本
  - `hugo version`
- `git clone https://github.com/arealclimber/ai-collaborative-blog.git`
- `cd ai-collaborative-blog`

# 新增文章

- `hugo new <DIR/FILE_NAME.md>`
  - 範例：`hugo new posts/test-article.md`
- 將預設值更改為以下內容：
  ```tsx
  ---
  title: "這篇文章的標題"
  date: 2024-06-22T19:37:20+08:00
  draft: false
  author: "作者名字"
  ---

  文章內容
  ```
- 在本地跑 hugo server
  - `hugo server`
- 刪掉 `public/` 資料夾，使用 `hugo` 重新 build

## 注意事項

- 如果 server 跑起來沒看到文章，可能是日期超過當下的時間
