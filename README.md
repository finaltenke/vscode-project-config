# ⚙️ Flutter 專案 VS Code 開發設定範本 (.vscode)

這是一份專門為 Flutter 專案設計的 VS Code 開發環境設定範本，包含常見的 `.vscode/` 配置檔案，方便快速建立一致的工作區設定、偵錯流程、自動化任務與程式碼片段等。

📆 適合用於 Flutter 個人開發、團隊專案初始設定，或作為範本進一步客製化。

## 📁 目錄結構與說明

```
.vscode/
🔘 settings.json             # Flutter/Dart 專用工作區設定（格式化、縮排、自動儲存等）
🔘 launch.json               # Flutter 應用程式偵錯設定
🔘 tasks.json                # Flutter 專案自動化任務（建構、測試、清除等）
🔘 global.code-snippets      # Flutter/Dart 程式碼片段，可快速輸入常用模板
🔘 extensions.json           # Flutter 開發推薦的 VS Code 擴充套件
```

## 🚀 快速開始

1. **下載或複製 `.vscode/` 資料夾**
```bash
git clone https://github.com/finaltenke/vscode-project-config.git
```
或直接把 .vscode 放進你的 Flutter 專案目錄下

2. 開啟 Flutter 專案時，VS Code 將自動套用設定，並提示安裝推薦的擴充套件

3. 可依照 Flutter 專案需求調整設定檔

## 🔧 功能亮點

✅ Flutter/Dart 專用格式設定
✅ Flutter 應用程式多環境偵錯設定
✅ Flutter 專案常用任務整合
✅ Flutter/Dart 程式碼片段快速輸入模板
✅ Flutter 開發必備擴充套件推薦

## ⚙️ 設定檔說明

### 1. Flutter 工作區設定 (settings.json)

`.vscode/settings.json` 檔案包含了 Flutter/Dart 專案的特定設定，以下是詳細說明：

**Flutter/Dart 基本設定：**
```json
{
    "dart.flutterSdkPath": ".fvm/versions/3.24.4",  // Flutter SDK 路徑，使用 FVM 管理
    "dart.sdkPath": ".fvm/versions/3.24.4",         // Dart SDK 路徑，與 Flutter SDK 相同
    "dart.lineLength": 120,                         // 程式碼每行最大長度
    "dart.showTodos": false                         // 是否顯示 TODO 註解
}
```

**Dart 檔案特定設定：**
```json
"[dart]": {
    "editor.formatOnSave": true,                    // 儲存時自動格式化
    "editor.formatOnType": false,                   // 輸入時不自動格式化
    "editor.rulers": [120],                         // 顯示 120 字元寬度參考線
    "editor.selectionHighlight": true,              // 高亮顯示選中文字的所有出現位置
    "editor.tabCompletion": "onlySnippets",         // Tab 鍵只觸發程式碼片段
    "editor.wordBasedSuggestions": "off"            // 關閉基於單字的建議
}
```

**Flutter 專案檔案排除設定：**
```json
"search.exclude": {                                 // 搜尋時排除的檔案
    "**/.fvm": true,                               // 排除 FVM 目錄
    "**/*.s.dart": false,                          // 包含 .s.dart 檔案
    "**/*.freezed.dart": true,                     // 排除 freezed 生成的檔案
    "**/*.g.dart": true                            // 排除其他生成的檔案
},
"files.watcherExclude": {                          // 檔案監視器排除的檔案
    "**/.fvm": true,
    "**/*.s.dart": true,
    "**/*.freezed.dart": true,
    "**/*.g.dart": true,
    "**/*.mock.dart": true                         // 排除測試用的 mock 檔案
},
"files.exclude": {                                 // 檔案總管中隱藏的檔案
    "**/*.mock.dart": true
}
```

**Flutter 專案自動化動作設定：**
```json
"editor.codeActionsOnSave": {                      // 儲存時執行的動作
    "editor.formatOnSave": "explicit",             // 明確要求才格式化
    "source.organizeImports": "explicit",          // 明確要求才整理 import
    "source.sortImports": "explicit",              // 明確要求才排序 import
    "source.fixAll": "explicit"                    // 明確要求才修復所有問題
}
```

**Flutter 專案檔案巢狀顯示設定：**
```json
"explorer.fileNesting.enabled": true,              // 啟用檔案巢狀顯示
"explorer.fileNesting.expand": false,              // 預設不展開巢狀檔案
"explorer.fileNesting.patterns": {                 // 檔案巢狀顯示規則
    "pubspec.yaml": ".metadata, pubspec.lock, analysis_options.yaml, .flutter-plugins, .flutter-plugins-dependencies",
    "*.dart": "$(capture).g.dart, $(capture).freezed.dart, $(capture).widgetbook.dart, $(capture).s.dart"
}
```

**其他 Flutter 開發相關設定：**
```json
"editor.wordWrapColumn": 120,                      // 自動換行寬度
"workbench.tree.indent": 15,                       // 檔案總管縮排寬度
"github.copilot.chat.codeGeneration.instructions": [  // GitHub Copilot 設定
    {
        "file": "copilot-instructions.md"
    }
]
```

**注意事項：**
- 這些設定專門針對 Flutter/Dart 專案優化
- 使用 FVM 管理 Flutter 版本
- 自動處理 Flutter 生成的檔案（.g.dart, .freezed.dart 等）
- 提供一致的 Flutter 程式碼格式和風格
- 優化 Flutter 專案檔案總管的顯示方式

### 2. Flutter 偵錯設定 (launch.json)

`.vscode/launch.json` 檔案中包含了 Flutter 應用程式的偵錯設定，支援多種執行模式：

**可用的 Flutter 執行模式：**
1. **一般模式**
   - 名稱：`app (MacOS)`
   - 用途：一般 Flutter 開發與測試
   - 特點：完整的 Flutter 開發工具支援

2. **效能分析模式**
   - 名稱：`app (MacOS) (profile mode)`
   - 用途：Flutter 效能測試與優化
   - 特點：啟用 Flutter 效能分析工具

3. **發布模式**
   - 名稱：`app (MacOS) (release mode)`
   - 用途：最終 Flutter 發布版本測試
   - 特點：最佳化 Flutter 執行效能

**Flutter 設定參數說明：**
```json
{
    "version": "0.2.0",                    // VS Code 偵錯設定版本
    "configurations": [
        {
            "name": "app (MacOS)",         // 設定名稱，顯示在 VS Code 偵錯下拉選單中
            "request": "launch",           // 啟動模式：launch（啟動新程序）或 attach（附加到現有程序）
            "type": "dart",                // 偵錯器類型：dart 用於 Flutter 應用程式
            "args": [                      // 傳遞給 Flutter 應用程式的命令列參數
                "-t",                      // 指定目標檔案
                "lib/main.dart",           // Flutter 主程式進入點
                "-d",                      // 指定目標裝置
                "macos",                   // 目標平台：macos、ios、android 等
                "--dart-define=APP_VENDOR=vd001",  // 定義環境變數：供應商識別碼
                "--dart-define=APP_ENV=uat"       // 定義環境變數：執行環境
            ],
            "flutterMode": "profile",      // Flutter 執行模式：debug（預設）、profile、release
        }
    ]
}
```

**Flutter 環境變數設定：**
- `APP_VENDOR`：Flutter 應用程式供應商識別碼
  - 用途：識別不同供應商的 Flutter 應用程式版本
  - 範例：vd001、vd002 等
- `APP_ENV`：Flutter 執行環境
  - 用途：指定 Flutter 應用程式的執行環境
  - 可用值：
    - `dev`：開發環境
    - `uat`：使用者驗收測試環境
    - `prod`：正式環境

**Flutter 環境變數使用範例：**
```dart
// 讀取環境變數
final String vendor = const String.fromEnvironment('APP_VENDOR');
final String env = const String.fromEnvironment('APP_ENV');

// 根據環境變數設定不同的 API 端點
String get apiBaseUrl {
  switch (env) {
    case 'dev':
      return 'https://dev-api.example.com';
    case 'uat':
      return 'https://uat-api.example.com';
    case 'prod':
      return 'https://api.example.com';
    default:
      return 'https://dev-api.example.com';
  }
}

// 根據供應商設定不同的 Flutter 應用程式名稱
String get appName {
  switch (vendor) {
    case 'vd001':
      return '供應商一號應用程式';
    case 'vd002':
      return '供應商二號應用程式';
    default:
      return '預設應用程式';
  }
}

// 在 Flutter Widget 中使用
class AppConfig extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text('目前環境：$env\n供應商：$vendor\nAPI 端點：$apiBaseUrl');
  }
}
```

**使用方式：**
1. 在 VS Code 中開啟 Flutter 專案
2. 點擊左側的「執行和偵錯」圖示
3. 從下拉選單中選擇需要的 Flutter 執行模式
4. 點擊「開始偵錯」或按 F5 開始執行

**注意事項：**
- 確保已安裝 Flutter 和 Dart 擴充套件
- 執行前確認 Flutter 目標裝置已連接（實體裝置或模擬器）
- 不同執行模式會影響 Flutter 應用程式的效能和除錯能力
- 環境變數可在 Flutter 程式碼中透過 `String.fromEnvironment()` 讀取
- 環境變數在 Flutter 編譯時就必須確定，不能在執行時動態修改

### 3. Flutter 程式碼片段 (global.code-snippets)

`.vscode/global.code-snippets` 檔案中定義了常用的 Flutter/Dart 程式碼片段，方便快速輸入常用模板。

**檔名轉換片段 (fnt)：**
- 用途：快速建立基於檔名的 Flutter/Dart 類別或變數
- 支援多種命名格式轉換

**使用方式：**
1. 在 VS Code 中建立新 Flutter/Dart 檔案，例如 `user_profile.dart`
2. 在編輯器中輸入 `fnt` 然後按 Tab 鍵
3. 程式碼片段會自動展開，並顯示轉換後的結果

**支援的轉換格式：**
- 原始檔名：顯示完整的檔案名稱（包含副檔名）
- 基礎名稱：去除副檔名後的檔案名稱
- PascalCase：將檔案名稱轉換為 PascalCase 格式（首字母大寫）
- camelCase：將檔案名稱轉換為 camelCase 格式（首字母小寫）

**範例：**
假設在 `user_profile.dart` 檔案中使用此片段，會產生：
```dart
// 原始檔名: user_profile.dart
// 提取基礎名稱: user_profile
// PascalCase 轉換: UserProfile
// camelCase 轉換: userProfile

// 使用範例:
class UserProfile extends StatelessWidget {
  final String userProfile;
  
  const UserProfile({super.key, required this.userProfile});
  
  @override
  Widget build(BuildContext context) {
    return Text(userProfile);
  }
}
```

### 4. Flutter 擴充套件推薦 (extensions.json)

`.vscode/extensions.json` 檔案用於推薦 Flutter 開發所需的 VS Code 擴充套件，方便團隊成員快速建立一致的開發環境。

**基本結構：**
```json
{
    "recommendations": [
        "Dart-Code.dart-code",           // Dart 語言支援
        "Dart-Code.flutter",             // Flutter 開發支援
        "felixangelov.bloc",            // BLoC 模式支援
        "robert-brunhage.flutter-riverpod-snippets",  // Riverpod 程式碼片段
        "usernamehw.errorlens",         // 錯誤提示增強
        "eamodio.gitlens",              // Git 歷史記錄增強
        "esbenp.prettier-vscode",       // Prettier 格式化支援
        "GitHub.copilot",               // GitHub Copilot AI 輔助
        "GitHub.copilot-chat"           // GitHub Copilot Chat 支援
    ]
}
```

**使用方式：**
1. 當其他開發者開啟 Flutter 專案時，VS Code 會自動提示安裝推薦的擴充套件
2. 可以點擊「安裝全部」快速安裝所有推薦的擴充套件
3. 也可以選擇性地安裝需要的擴充套件

**注意事項：**
- 建議只包含 Flutter 開發真正需要的擴充套件
- 定期更新擴充套件清單，移除不再使用的擴充套件
- 考慮團隊成員的 Flutter 開發需求，避免推薦過多不必要的擴充套件

### 5. Flutter 自動化任務 (tasks.json)

`.vscode/tasks.json` 檔案定義了常用的 Flutter 自動化任務，方便快速執行常見的開發操作。

**基本結構：**
```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Flutter: 清理專案",
            "type": "shell",
            "command": "flutter clean",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            }
        },
        {
            "label": "Flutter: 取得套件",
            "type": "shell",
            "command": "flutter pub get",
            "group": "build",
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            }
        },
        {
            "label": "Flutter: 執行測試",
            "type": "shell",
            "command": "flutter test",
            "group": "test",
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            }
        }
    ]
}
```

**使用方式：**
1. 使用命令面板（Cmd/Ctrl + Shift + P）
2. 輸入 "Tasks: Run Task"
3. 選擇要執行的 Flutter 任務

**常用 Flutter 任務說明：**
- **清理專案**：執行 `flutter clean`，清除 Flutter 建置快取
- **取得套件**：執行 `flutter pub get`，更新 Flutter 相依套件
- **執行測試**：執行 `flutter test`，運行 Flutter 單元測試

**注意事項：**
- Flutter 任務可以設定相依關係，確保按正確順序執行
- 可以設定任務的顯示方式（always、never、silent）
- 建議為 Flutter 任務提供清楚的標籤和說明

## 📌 注意事項

- 此設定專門針對 Flutter 專案優化，可依需調整
- global.code-snippets 包含 Flutter/Dart 通用片段，可提拔為特定語言片段
- 請自行檢查是否與現有 Flutter 專案設定衝突

## 🙌 謝謝使用

此頁面主要用於開放分享 Flutter 專案常用的 VS Code 開發環境設定，也歡迎 Fork 或 Clone 作為自己 Flutter 專案的基礎配置！

## 💼 License

MIT License

Made with ❤️ by finaltenke

