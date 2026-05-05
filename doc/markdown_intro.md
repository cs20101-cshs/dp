# Markdown 簡介
版本：v1.1

本文件係給竹山高中資處科學生介紹 Markdown 標記語言之用。

## 為何要學 Markdown？
- **因為要用 GitHub**，每個 README.md 都是用 Markdown 寫的。
- 用 Markdown 可以很直覺且「看起來」很專業地把自己的想法寫出來，而且簡單、快速、排起來又不難看。
- 號稱資字輩的人多少要會一點這種工程師慣用的文件格式，否則感覺上就不是圈子裡的人......（以下省略八千字）

## Markdown 語法
Markdown 雖然簡單，功能並不小，所以有些網站教學會講得太複雜。基本上，一開始只要掌握幾個基本用法就可以了：
1. 標題
2. 粗、斜體
3. 列表（有序、無序、層級）
4. 超連結 / 圖片（路徑設定大考驗！）
5. 引用 / 程式碼區塊
6. 分隔線

因此，看來看去，最適合給同學入門的 Markdown 教學網站在這裡，比我上面提的還深入一點點，但又不會講太多：
[工程師阿穆 -- Markdown 語法完整教學](https://homuchen.com/posts/markdown-tutorial/)

## Markdown 工具
1. [GitHub](https://github.com/)
可以直接在 GitHub 上面寫 Markdown，不過老師比較習慣在上面稍微修改，不習慣拿來寫整篇。

2. [HackMD](https://hackmd.io/)
一個完全以 Markdown 構成的分享空間，可以用得非常深入。適合大家一起用（小組共筆、社團筆記、活動紀錄等），也可以拿來自己用（整理課堂筆記、自主學習紀錄）。

3. [Markdown Editor simple](https://apps.microsoft.com/detail/9n614lmtjg5h?hl=zh-TW&gl=TW)
Windows 平台的簡單 Markdown 編輯器。特色是畫面左邊寫 Markdown 語法，右邊馬上呈現結果。適合初學。

4. [Visual Studio Code](https://code.visualstudio.com/)
簡稱 VS Code，極為強大但也有些複雜的跨語言程式開發平台，拿來寫 Markdown 其實是程式設計師的「順便」。由於 APCS 考試時不能用，所以老師基本上不會教你怎麼用 XDDDDD

## Markdown 範例
以下可以當作你 GitHub 儲存庫（repository，簡稱 repo）根目錄下 README.md 的範本，可以拷去改，但至少要註明：
1. 這個 repo 是做什麼用的
2. 目前放了哪些資料夾和檔案
3. 你自己寫了什麼、改了什麼、學到了什麼
```
# 我的作品集

## 自我介紹
我是竹山高中資處科學生○○○，正在學寫程式和資安，老師要我開 GitHub 給他看。

## 作品集網址
[我的 GitHub](https://github.com/cs20101-cshs/dp)

## repo 內容
- `python/`：Python 程式，包括作業和刷題
- `ctf/`：打 CTF 的解題 write-up
- `note/`：讀書筆記
```
