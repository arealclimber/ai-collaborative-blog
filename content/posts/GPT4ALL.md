---
title: 'GPT4ALL'
date: 2024-07-24T10:22:29+08:00
draft: false
author: 'Daniel'
---

# GPT4ALL

## 前言

GPT4All可以桌機和筆電上較方便地運行本地端的大型語言模型。使用者無需調用API或升級GPU，只需下載應用程序即可開始使用。 

- 網站: https://www.nomic.ai/gpt4all
- 文件: https://docs.gpt4all.io/index.html
- Github: https://github.com/nomic-ai/gpt4all
- 其他資源: [不用網路！在電腦安裝類 ChatGPT 的 AI，還指定對話的文件（GPT4All）](https://medium.com/dean-lin/%E5%9C%A8%E9%9B%BB%E8%85%A6%E5%AE%89%E8%A3%9D%E9%A1%9E-chatgpt-%E7%9A%84-ai-%E9%82%84%E5%8F%AF%E4%BB%A5%E4%B8%8A%E5%82%B3%E6%96%87%E4%BB%B6%E5%B0%8D%E8%A9%B1-gpt4all-80d32c84b37a)

## 當下版本

3.0.0

## 收費方式

免費

## 如何安裝

1. 到官網下載對應作業系統的安裝檔
2. 安裝GPT4ALL
3. 安裝後首次啟動GPT4ALL時，會被詢問是否要分享資料給GPT4ALL作改善，不想的話請都選NO

## 如何使用

### 如何使用Chats功能?

1. 到Models分頁
2. 點擊`+ Add Model`，查看清單或透過搜尋功能找到想要用的模型
3. 點擊`Download`，下載模型到電腦中(預設路徑是`C:/Users/user/AppData/Local/nomic.ai/GPT4All/`，也可以到設定裡更改)
4. 等待下載完成後，到Chats分頁選擇模型
5. 開始聊天
6. (可選)到Settings分頁的Model中修改Prompt或微調模型的hyperparameter

### 如何使用LocalDocs功能?

1. 到LocalDocs分頁
2. 點擊`+ Add Doc Collection`
3. 幫新的Collection取名並選擇資料夾路徑(之後會用該資料夾內含的.txt/.pdf/.md檔案做RAG)
4. 點擊`Create Collection`，等待embedding處理完成
5. embedding完成後，到Chats分頁選擇模型
6. 點擊右上角的`LocalDocs`，選擇要用哪個Collection
7. 開始聊天
8. (可選)到Settings分頁的LocalDocs中修改設定，再回來點擊`Rebuild`重新embedding
9. (可選)修改或更新資料夾中的檔案，再回來點擊`Rebuild`重新embedding

## Q&A

### GPT4All支援哪些語言模型？

GPT4All支援已上傳到 HuggingFace 並具備 llama.cpp 實現的模型。

> llama.cpp 是一個用於高效地運行和管理機器學習模型的開源庫，它提供了對各種語言模型的支持，使得這些模型可以在不同的平台上運行，比如 Windows、Mac 和 Linux。通過使用 llama.cpp，這些模型可以更有效地執行和使用計算資源。

### GPT4All支援哪些嵌入模型？

GPT4All支援 SBert 和 Nomic Embed Text v1 & v1.5。

### GPT4All需要搭配什麼軟體？

你只需要在 Windows、Mac 或 Linux 電腦上安裝 GPT4all。

### GPT4All支援哪些 SDK 語言？

GPT4All的 SDK 使用 Python 以提高可用性，但這些是圍繞 llama.cpp 實現的輕量級綁定。

### GPT4All是否有 API？

是的，你可以使用GPT4All的 OpenAI 兼容 API 以伺服器模式運行模型，你可以在設置中進行配置。

### 我能監控 GPT4All 部署嗎？

可以，GPT4All 與 OpenLIT 整合，因此你可以自動監控用戶互動和硬體使用情況，以達到完整的可觀察性。

> OpenLIT是一個原生於OpenTelemetry的工具，旨在幫助開發者瞭解他們在生產環境中LLM應用的性能。它會自動收集LLM的輸入和輸出元數據，並監控自主部署的LLM的GPU性能。

### 是否有命令行界面 (CLI)？

有的，GPT4All提供了輕量級的 Python 客戶端作為 CLI。

### 我需要什麼硬體？

GPT4All 可以在 CPU、Metal (Apple Silicon M1+) 和 GPU 上運行。

### 系統需求是什麼？

你的 CPU 需要支持 AVX 或 AVX2 指令集，並且需要足夠的 RAM 來將模型加載到記憶體中。
