---
title: 'Copilot'
date: 2024-07-20T18:35:35+08:00
draft: true # 隱藏 AI 工具文章
author: 'Winnie'
---

## Introduction

![What is copilot](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*KiWliV0t7Kl3FgaamNX_tw.png)

Copilot 是 GitHub 推出的 AI 程式碼工具，基於 OpenAI 加上 GitHub 上大量的原始碼，使用的是 GPT-4 Turbo。

官網聲稱可以達到四成以上的正確率，也就是說可以少寫四成以上的程式碼。

## Insatll

目前非免費，可參考此份連結進行安裝：https://code.visualstudio.com/docs/copilot/setup

## Usage

* 上下文 (Conetext)
    * 當前編輯的程式檔案
    * 已經開啟的檔案分頁
    * 變數命名
    * 註解
* CDD (Comment-Driven Development)
    * 透過註解來開發
    * 提供良好示範

### Code Suggestions

`control + enter` 會打開 copilot 的建議視窗，不止一種 Suggestion。

### Generate Commit Message

自動產生符合的 Commit Message。

### Chat

* 類似於 Chat-GPT
* 會跟當前滑鼠所在的程式碼自動關聯

有三種用指令開啟對話的方式：

* 位於游標位置的聊天視窗： `command + I`
* 位於視窗正上方的聊天視窗： `command + shift + I`
* 位於視窗側邊欄的聊天視窗： `command + control + I`

#### Command

* `/tests`：寫 test
* `/explain`：解釋程式碼
* `/fix`：修復錯誤程式碼
* `@terminal`：給出 terminal 指令
