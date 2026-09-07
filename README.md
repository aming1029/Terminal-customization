# Windows Terminal 美化说明教程
# 本仓库旨在美化windows终端 使其拥有亚克力效果

## 一、将 CMD 默认终端改为 Windows Terminal（可选）

在当前用户注册表中修改以下位置：

    HKCU\Console\%%Startup

设置以下两个字符串值：

| 名称  | 数据  |
| --- | --- |
| `DelegationConsole` | `{2EACA947-7F5F-4CFA-BA87-8F7FBEEFBE69}` |
| `DelegationTerminal` | `{2EACA947-7F5F-4CFA-BA87-8F7FBEEFBE69}` |

这两个值是 Windows Terminal 的标识符 设置后，从运行窗口、资源管理器地址栏等位置启动 `cmd` 时，会默认在 Windows Terminal 中打开

## 二、Windows Terminal 配置文件

Windows Terminal 的配置文件位置为：

    %LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json

建议修改前先备份 `settings.json` 如果使用 Windows Terminal Preview，请使用对应的 Preview 配置目录

## 三、亚克力效果配置

在 `profiles.defaults` 中加入或修改以下配置：

    {
      "useAcrylic": true,
      "acrylicOpacity": 0.6,
      "opacity": 82
    }

配置说明：

* `useAcrylic: true`：开启亚克力背景效果
* `acrylicOpacity: 0.6`：降低背景层不透明度，使桌面背景的模糊效果更明显
* `opacity: 82`：设置窗口整体透明度

## 四、字体配置

在 `profiles.defaults` 或指定的 `cmd` 配置中加入：

    {
      "fontFace": "Cascadia Mono",
      "fontSize": 15,
      "fontWeight": "semi-bold"
    }

字体使用 `Cascadia Mono`，字号为 15，半粗体用于提高可读性

## 五、淡紫色主题配置

创建一个自定义配色方案，并将它应用到 `cmd` 配置：

    {
      "name": "淡紫亚克力",
      "background": "#7F6D8D",
      "foreground": "#FFFFFF",
      "cursorColor": "#FFFFFF",
      "selectionBackground": "#B9A6C5"
    }

同时在 `profiles.defaults` 或 `cmd` 配置中指定：

    {
      "colorScheme": "淡紫亚克力",
      "background": "#7F6D8D",
      "foreground": "#FFFFFF",
      "cursorColor": "#FFFFFF"
    }

白色文字与淡紫色背景形成较高对比度，可以保持文字清晰

## 六、配置生效

1. 保存 settings.json
2. 关闭没有更新样式的旧标签页
3. 重新打开终端

## 七、备份与恢复

修改配置前建议复制一份 `settings.json`，例如：

    settings.json.backup

需要恢复时，关闭 Windows Terminal，再将备份文件改回 `settings.json`
