# vscode-config
vscode 設定檔，包含：
  1. 設定 `setting.json`
  2. 鍵盤快捷鍵 `keybindings.json`
  3. 程式碼片段 `dart.json`
  4. UI狀態 `globalState.json`
  5. 延伸模組：vscode 套件

## 恢復設置：
  1. 左下角齒輪 > 設定檔（預設）> 匯入設定檔
  2. 點擊 `選取檔案...`
  3. 選取 `vscode.code-profile` 檔案
  4. 點擊 `建立設定檔`

## Code Snippets
範例：
```json
{
    "snippet 標題": {
        "prefix": "snippet prefix, 即快捷鍵",
        "body": [
            "snippet body",
            "這裡是第二行",
            "\t這樣是縮排"
        ],
        "description": "snippet description"
    }
}
```
> - "snippet 標題"：程式碼片段的名稱（置換修改）。
> - "prefix"：當你輸入這個前綴時，程式碼片段將被觸發。
> - "body"：程式碼片段的內容，可以是多行程式碼。
> - "description"：程式碼片段的描述，用於提示和說明。
