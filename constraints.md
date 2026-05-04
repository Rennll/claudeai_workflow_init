# constraints.md — 使用者環境與限制

## 平台
- claude.ai 網頁版（主要）及手機 App
- 有 Claude Project 功能，上限 5 個

## 本機環境
- Windows 10，本機使用 PowerShell 7工作場所使用Powershell 5.1，預設編碼 cp950，輸入輸出一律使用 UTF-8
- Python：工作場所 3.10，使用uv。自用筆電 3.11，使用pvenv-win
- Node.js 24：僅自用筆電
- 工作場所不額外安裝軟體，方案需在現有環境內解決

## 開發架構
- 開發在雲端（claude.ai session）：產出程式碼、在容器內執行與測試
- 部署在本機：運行最終成果
- Git 用於版本管理