---
title: 'Cursor'
date: 2024-08-10T17:42:01+08:00
draft: true # 隱藏 AI 工具文章
author: 'Daniel'
tags: ['']
---

# Cursor使用說明

## 簡介

- Cursor 是一款內建 AI 輔助的編輯器。
- Cursor 基於 VS Code 開發而成，因此能直接移植使用者在 VS Code 的設定或延伸套件。
- Cursor 的設定分成"Cursor AI 相關的設定"和"VS Code 的設定"兩種。
- Cursor 選擇做為一款編輯器而非 VS Code 的延伸套件，是因為這樣可以得到更大的 UI 控制權，開發更適用於 AI 的使用者體驗。
- Cursor 選擇把 Activity Bar 做成橫的，是為了保留空間給 Cursor Chat 功能，但使用者也可以去"VS Code 設定"中的`workbench.activityBar.orientation`把它改成傳統的直式 Activity Bar。

## 收費方式

![Pasted image 20240807224748](https://github.com/user-attachments/assets/3f0d3a00-5355-4391-ab75-93c557252cc8)

- Fast/Slow Requests : 預設情況下，Cursor 伺服器會嘗試為所有使用者提供快速的`premium`模型請求。然而，在高峰期間，當使用者的快速`premium`使用量耗盡後，將會被轉移到一個緩慢的池中，這基本上是一個等待快速`premium`請求的使用者隊列。這個隊列是公平的，Cursor會竭盡所能地保持隊列盡可能短。然而，如果您需要更多的快速`premium`使用量且不想等待，您可以在設置頁面中添加更多請求。
- 登入 Cursor 官網後，可以到 `Settings` 頁面查看目前的使用量。
- Cusor 也可以改成按用量計費的模式，這個模式還能設定使用量上限避免爆預算。(這部分沒查到費用)

## LLM模型

![Pasted image 20240807224903](https://github.com/user-attachments/assets/074903dc-fc7a-46fa-918e-eded93793c44)

## 功能

### Cursor Tab

- 在當前游標位置的前一行到後兩行之間的範圍，Cursor 會視情況提供程式碼建議，使用者可以選擇按`Tab`接受這個建議，或按`Esc`拒絕這個建議。
- 接受建議後，Cursor 還會預測使用者接下來可能會想把游標移到某行，按`Tab`可以接受快速跳去該行。
- Tab 功能也可以在 VS Code 的"Go to Definition" 或 "Go to Type Definition"的 peek views 中使用。
- 編輯器的右下角可以對 Tab 功能做設定。

### Cursor Chat

- 透過指定不同的 *context* (情境)，Cursor 可以基於 context 指定的範圍回覆使用者問題。
- Cursor 預設的 context 是"current file"，即針對當前開啟的檔案做回覆。要調整 context 的話要在文字框中用`@`符號做選擇。詳細`@`符號的用法請見[這裡](https://docs.cursor.com/context/@-symbols/basic)。
- Chat 是在 *AI pane* 中進行(即右邊的側邊欄)，使用`Ctrl + L`可以快速開啟或關閉。
- 同一系列的聊天內容稱為 *chat thread*，Cursor 有提供歷史紀錄的功能讓使用者可以回顧較舊的 chat thread，也可以重新命名或刪除 chat thread。
- 對於 linter error，Cursor 提供"AI Fix in Chat"功能讓使用者可以一鍵詢問怎麼解決error。
- 對於 Codebase 類型的 context，建議先對整個專案目錄做 *Codebase indexing* (即 embedding )，提高聊天回覆的準確度。在`Cursor Settings` > `Features` > `Codebase Indexing`可以確認目前 indexing 的進度。
- AI pane 中生成的程式碼，可以用`Apply`一鍵導入程式檔案中，導入後會以類似 Git diff 的格式呈現，使用者可以選擇以下動作: 
	- `Ctrl + Enter`接受所有變更
	- `Ctrl + Backspace`拒絕所有變更
	- `Ctrl + Shift + Y`接受某段落的變更
	- `Ctrl + N`拒絕某段落的變更

### Cursor Cmd K

- 也叫 Ctrl K，相較 Cursor Chat 是在側邊欄運作，Cmd K 則是在編輯視窗中運作，使用者可以更方便地用 AI 輔助編輯程式。
- 用`Ctrl + K`可以啟動 *prompt bar*，prompt bar 也可以像 Cursor Chat 一樣在文字框中用`@`符號調整 context 。
- 用游標圈選想要針對的程式碼段落再啟動 prompt bar，可以對既有程式碼做編輯；反之若在沒有圈選程式碼的時候啟動 prompt bar，Cursor 會視為要生成程式碼。
- 在 prompt bar 中點擊`Alt + Enter`，可以啟動 *quick question*，用來針對游標圈選的內容問任何問題，而非做程式碼編輯。
- Cmd K 也支援在 Cursor 的終端機中使用，協助使用者生成命令。

### 情境設定

- 從`Cursor Settings` > `General` > `Rules for AI`可以設定公用的 prompt，這個 prompt 將套用到 Cursor Chat 和 Cursor Cmd K。
- Ruls for AI 可以到[這裡](https://forum.cursor.com/t/share-your-rules-for-ai/2377)參考其他人的寫法。
- 如果想針對某個專案制定客制的 prompt，可以在專案根目錄創建一個名為`.cursorrules`的檔案並撰寫內容。

### Context選擇

- `@`符號提供多種情境讓使用者下指令時做搭配，其中有些只能在 Cursor Chat 中使用、有些只能在 Cursor Cmd K 中使用。
- `@File`：此情境會讓 Cursor 去參考某個檔案的內容來回覆使用者，可搭配`@Code`近一步指定某段程式碼。
- `@Folder`：此情境會讓 Cursor 去參考某個資料夾的內容來回覆使用者。(Cursor Chat only)
- `@Code`：此情境會讓 Cursor 去參考某段程式碼的內容來回覆使用者。
- `@Ｄocs`：此情境會讓 Cursor 去參考某個文件的內容來回覆使用者，到`Cursor Settings` > `Features` > `Docs`可以對文件做新增/刪除等進階設定。
- `@Git`：此情境會讓 Cursor 去參考 Git 版本控制的內容來回覆使用者，此外可以用`@Diff of Working State`來生成 Git Commit Message。(Cursor Chat only)
- `@Codebase`：此情境會讓 Cursor 去參考整個專案的內容來回覆使用者。
- `@Web`：此情境會讓 Cursor 去參考網路上的資訊來回覆使用者。
- `@Chat`：此情境會讓 Cursor 去參考當前 chat thread 的內容來回覆使用者。(Cursor Cmd K only)
- `@Definitions`：此情境會讓 Cursor 去參考當前 Cmd K 範圍相關的程式定義的內容來回覆使用者。(Cursor Cmd K only)
- Paste Links：此情境會讓 Cursor 去參考貼上的超連結的內容來回覆使用者。
