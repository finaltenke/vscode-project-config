# ⚙️ VS Code 開發設定範本 (.vscode)

這是一份用於 VS Code 的開發環境設定範本，包含常見的 `.vscode/` 配置檔案，方便快速建立一致的工作區設定、偵錯流程、自動化任務與程式碼片段等。

📆 適合用於個人開發、團隊專案初始設定，或作為範本進一步客製化。

## 📁 目錄結構與說明

```
.vscode/
🔘 settings.json             # 工作區專用設定（格式化、縮排、自動儲存等）
🔘 launch.json               # 偵錯器啟動設定（例如 Node.js 或 Python）
🔘 tasks.json                # 自動執行件務（建構、測試、清除等）
🔘 global.code-snippets      # 自訂程式碼片段，可快速輸入常用模板
🔘 extensions.json           # 推薦安裝的 VS Code 擴充套件
```

## 🚀 如何使用

1. **下載或複製 `.vscode/` 資料夾**

```bash
git clone https://github.com/finaltenke/vscode-project-config.git
```
或直接把 .vscode 放進你的專案目錄下

2. 開啟專案時，VS Code 將自動套用設定，並提示安裝推薦的擴充套件

3. 可依照專案需求調整設定檔

## 🔧 功能亮點

✅ 統一格式設定（支援 Prettier / ESLint）

✅ 支援 Node.js / Python 等語言偵錯範例

✅ 常用 Tasks 與 Scripts 整合

✅ 程式碼片段快速輸入模板

✅ 擴充套件推薦，快速建立熟悉的開發環境

## 📌 注意事項

- 此設定以個人開發習慣為基礎，可依需調整

- global.code-snippets 為多語言通用片段，可提拔為特定語言片段

- 請自行檢查是否與現有專案設定衝突

## 🙌 謝謝使用

此頁面主要用於開放分享我自己常用的 VS Code 開發環境設定，也歡迎 Fork 或 Clone 作為自己專案的基礎配置！

## 💼 License

MIT License

Made with ❤️ by finaltenke

