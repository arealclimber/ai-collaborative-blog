# 初始化

## 步驟 1：安裝 Hugo

- 根據不同作業系統安裝 Hugo，參考[官方文件](https://gohugo.io/installation/)
- 確保 Hugo 安裝成功，可輸入指令查看版本：
  - `hugo version`

## 步驟 2：克隆倉庫

1. 使用以下命令克隆倉庫：
   - `git clone https://github.com/arealclimber/ai-collaborative-blog.git`
2. 進入倉庫目錄：
   - `cd ai-collaborative-blog`

## 步驟 3：初始化 Hugo 主題

1. 克隆倉庫之後，`./themes/PaperMod` 會是空的，需要依序執行以下指令安裝主題：
   - `git submodule init`
   - `git submodule update`
2. 此時主題檔案應已經安裝在 `./themes/PaperMod` 資料夾中。

# 新增文章

- 整個流程為：寫文章 → 生成靜態文件 & 跑本地伺服器查看是否更新文章 → 將更新推到遠端 → 查看 GitHub 自動部署是否成功、網站是否已更新新文章。

## 步驟 1：寫文章

1. 創建文章：
   - `hugo new <DIR/FILE_NAME.md>`
   - 範例：`hugo new posts/test-article.md`
2. 執行完指令後，`test-article.md` 會得到以下內容：

   ```tsx
   +++
   title: 'Test Article'
   date: 2024-06-23T20:49:50+08:00
   draft: true
   author: ''
   +++

   ```

3. 將預設值的 `+++` 更改為 `---`，在作者欄加上自己的名字，並在文章完成後將 `draft` 改為 `false`：

   ```tsx
   ---
   title: 'Test Article'
   date: 2024-06-23T20:49:50+08:00
   draft: false
   author: "作者名字"
   ---

   開始寫文章....

   ```

## 步驟 2：生成靜態文件 & 跑本地伺服器查看是否更新文章

1. 生成靜態文件：
   - `hugo`
2. 在本地運行 Hugo 伺服器查看動態變化：
   - `hugo server`
3. 在 commit 以前需確保靜態文件是正式網域，而非 localhost，所以須停止 Hugo 伺服器並且再重新生成靜態文件：
    - `hugo`

## 步驟 3：將更新推到遠端

1. 添加所有變更：
   - `git add .`
2. 提交變更：
   - `git commit -m "YOUR_COMMIT_MESSAGE"`

## 步驟 4：查看 GitHub 自動部署是否成功、網站是否將新文章更新上來

1. [查看自動部署紀錄](https://github.com/arealclimber/ai-collaborative-blog/deployments/Production)
2. [查看網站](https://ai-co-blog.vercel.app/)

## 注意事項

- 如果伺服器運行起來沒看到文章，可能是日期超過當下的時間。
