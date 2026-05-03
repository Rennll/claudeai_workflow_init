# constraints.md — 使用者環境與限制

## 平台
- claude.ai 網頁版（主要）及手機 App
- 有 Claude Project 功能，上限 5 個

## 本機環境
- Windows 10 + PowerShell 7，預設編碼 cp950，輸入輸出一律使用 UTF-8
- Python：工作場所 3.10、自用筆電 3.11
- Node.js 24：僅自用筆電
- 工作場所不額外安裝軟體，方案需在現有環境內解決

## 開發架構
- 雲端容器（claude.ai session）為主力執行環境
- 本機為輕量同步站，只跑非在本地不可的任務
- GitHub 作為中繼，串接雲端產出與本機
- Git 用於版本管理與同步，成果需手動複製下載或透過 GitHub 網頁操作