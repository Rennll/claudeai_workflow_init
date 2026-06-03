# constraints.md — 使用者環境與限制

## 平台
- claude.ai 網頁版（主要）及手機 App
- 有 Claude Project 功能，上限 5 個

## 本機環境
- Windows 10，本機使用 PowerShell 7工作場所使用Powershell 5.1，預設編碼 cp950，輸入輸出一律使用 UTF-8
- Python：工作場所 3.10，使用pvenv-win。自用筆電 3.11，使用uv
- Node.js 24：僅自用筆電
- 工作場所不額外安裝軟體，方案需在現有環境內解決

## 開發架構
- 開發在雲端（claude.ai session）：產出程式碼、在容器內執行與測試
- 部署在本機：運行最終成果
- Git 用於版本管理

## 階段偵測與升級

### 階段定義
- **探索**：討論想法、可行性，方向未定
- **成形**：方向確定，開始討論怎麼做
- **簡單跨 session**：有後續要做，但複雜度低
- **完整專案**：持續迭代、決策多、需要長期維護

### 偵測與提示規則
- 探索→成形：偵測到「方向確定、開始討論實作」時，詢問是否需要帶入 constraints.md
- 任何階段結束時：偵測到「這個 session 有後續」，主動產出 handoff
- 成形或跨 session→完整專案：偵測到「複雜度高、會持續迭代」，提示是否建立 project.md 與 Claude Project

### Handoff 格式
- **輕量**（簡單跨 session）：背景概論、關鍵決策、下一步，格式不固定
- **完整**（完整專案）：依照 bootstrap.md 的 handoff.md 格式

### Context Window 管理
當對話累積到一定長度、或話題告一段落時，主動提示是否需要 wrap-up 並產出 handoff。

## 設定維護

### 剪枝規則
使用者主動要求時，掃描 protocol.md 與 constraints.md：
- 找出重複或互相矛盾的規則
- 找出從未被觸發過的規則
- 合併或刪除，產出草稿後等使用者確認