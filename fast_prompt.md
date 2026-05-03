# 下次遇到 prompt 不動時的排查順序

今天的排查走過這幾個關卡，整理成下次能快速重現的順序：

**第一步，確認 profile 路徑和檔案存在**
```powershell
$profile
Test-Path $profile
```
路徑錯或檔案不在，後面都不用查了。

**第二步，確認執行權限**
```powershell
Get-ExecutionPolicy
```
要 `RemoteSigned` 或更寬鬆，`Restricted` 的話 profile 根本不會跑。

**第三步，手動載入 profile，看有沒有報錯**
```powershell
. $profile
```
沒輸出不代表成功，只代表沒有明顯錯誤。

**第四步，確認 prompt 函數有沒有被定義**
```powershell
$function:prompt
```
有內容就代表載入成功，這時問題出在執行期；空白就表示 dot-source 本身有問題。

**第五步，直接呼叫 prompt，讓執行期錯誤浮出來**
```powershell
prompt
```
今天的 regex 語法錯誤就是在這步才現形的——因為問題藏在函數內部，載入時不會觸發。

**第六步，如果有外部檔案（像 FastPrompt.ps1），單獨載入它**
```powershell
. "$env:USERPROFILE\FastPrompt.ps1"
```
把範圍縮小，確認問題出在 profile 本身還是它引入的模組。

今天沒用到但值得備著的是 `$host.Name`，用來確認宿主程式有沒有偷偷覆蓋 prompt 函數。