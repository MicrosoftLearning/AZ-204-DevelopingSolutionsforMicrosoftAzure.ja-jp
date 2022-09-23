# <a name="lab-virtual-machine-setup"></a>ラボ仮想マシンのセットアップ

## <a name="installed-software"></a>インストール済みソフトウェア

| ソフトウェア | Link |
| --- | --- |
| Windows 10 (ビルド 2004) | <https://www.microsoft.com/software-download/windows10> |
| Visual Studio Code | <https://code.visualstudio.com> |
| Visual Studio Code 用の Azure Account 拡張機能 | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account> |
| Visual Studio Code 用の Azure Functions 拡張機能 | <https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions> |
| Visual Studio Code 用の Azure Resource Manager 拡張機能 | <https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools> |
| Visual Studio Code 用の Azure CLI ツール拡張機能 | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.azurecli> |
| Visual Studio Code PowerShell 拡張機能 | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell> |
| Visual Studio Code C# 拡張機能 | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp> |
| PowerShell 7 | <https://github.com/PowerShell/PowerShell/releases/tag/v7.0.3> |
| .NET 6 SDK | <https://dotnet.microsoft.com/download/dotnet/6.0> |
| Azure PowerShell | <https://docs.microsoft.com/powershell/azure/install-az-ps> |
| Azure CLI | <https://docs.microsoft.com/cli/azure/install-azure-cli> |
| Azure Storage Explorer | <https://azure.microsoft.com/features/storage-explorer> |
| .NET ツール - HttpRepl | <https://github.com/dotnet/HttpRepl> |
| Azure Functions Core Tools | <https://docs.microsoft.com/azure/azure-functions/functions-run-local#v3> |
| Windows ターミナル | <https://aka.ms/terminal> |
| Edge (Chromium) | <https://www.microsoft.com/edge> |

## <a name="additional-configuration"></a>その他の構成

- ClearType を有効にする
  
- 既定のブラウザーとして Microsoft Edge を構成する

- VSCode 構成を更新する

  ```json
  {
    "editor.fontFamily": "'Cascadia Code', Consolas, 'Courier New', monospace",
    "update.enableWindowsBackgroundUpdates": false,
    "update.mode": "manual",
    "terminal.integrated.shell.windows": "C:\\Program Files\\PowerShell\\7\\pwsh.exe",
    "workbench.startupEditor": "none",
    "terminal.integrated.rendererType": "dom",
    "csharp.suppressDotnetInstallWarning": true,
    "csharp.suppressDotnetRestoreNotification": true,
    "csharp.supressBuildAssetsNotification": true,
    "azureFunctions.showProjectWarning": false
  }
  ```

- Windows ターミナル構成を更新する

  ```json
  {
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
    "profiles": [
      {
        "guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
        "useAcrylic": true,
        "acrylicOpacity": 0.85,
        "colorScheme": "Campbell",
        "fontFace": "Cascadia Code",
        "hidden": false,
        "name": "PowerShell",
        "source": "Windows.Terminal.PowershellCore"
      },
      {
        "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
        "hidden": false,
        "name": "Azure Cloud Shell",
        "source": "Windows.Terminal.Azure"
      }
    ],
    "schemes": [],
    "keybindings": []
  }
  ```

- [スタート] メニューとタスクバーは、次のアイコンのみを含むように構成してください。
  - エクスプローラー
  - Edge
  - Windows ターミナル
  - Visual Studio Code
  - Azure Storage Explorer

- PowerShell 7 更新通知を無効にする

  1. ``POWERSHELL_UPDATECHECK`` という名前の[環境変数を作成する](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)
  
  1. 環境変数の値を ``Off`` に設定する (大文字と小文字は区別される)

- Windows ファイアウォールを構成するために Azure Functions Core Tools を少なくとも 1 回実行する

  ```bash
  func init test --worker-runtime dotnet
  cd test
  func new --template 'HTTP trigger' --name web
  func start --build
  ```
