---
title: windows-terminal-config
date: 2019-11-11 17:10:50
categories:
- [Windows, Tools]
tags:
- terminal
- windows
---

# 配置文件

```json
{
    // 全局设置
    "globals": {
        "alwaysShowTabs": true,
        "copyOnSelect": false,
        // 默认终端的guid
        "defaultProfile": "{1c4de342-38b7-51cf-b940-2309a097f589}",
        "initialCols": 100,
        "initialRows": 25,
        // 快捷键
        "keybindings": [],
        "requestedTheme": "system",
        "showTabsInTitlebar": true,
        "showTerminalTitleInTitlebar": true,
        "wordDelimiters": " ./\\()\"'-:,.;<>~!@#$%^&*|+=[]{}~?\u2502"
    },
    // 终端配置
    "profiles": [
        {
            // 透明度
            "acrylicOpacity": 0.75,
            "background": "#111111",
            "closeOnExit": true,
            // 颜色主题
            "colorScheme": "MaterialDark",
            // 终端启动命令
            "commandline": "powershell.exe",
            "cursorColor": "#FFFFFF",
            "cursorShape": "bar",
            // 字体
            "fontFace": "Consolas",
            "fontSize": 12,
            "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
            "historySize": 9001,
            // 显示的名称
            "name": "Windows PowerShell",
            "padding": "5, 5, 5, 5",
            "snapOnInput": true,
            // 开始位置
            "startingDirectory": "%USERPROFILE%",
            // 毛玻璃效果
            "useAcrylic": true
        },
        {
            "acrylicOpacity": 0.75,
            "closeOnExit": true,
            "colorScheme": "MaterialDark",
            "commandline": "cmd.exe",
            "cursorColor": "#FFFFFF",
            "cursorShape": "bar",
            "fontFace": "Consolas",
            "fontSize": 12,
            "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
            "historySize": 9001,
            "icon": "ms-appx:///ProfileIcons/{0caa0dad-35be-5f56-a8ff-afceeeaa6101}.png",
            "name": "cmd",
            "padding": "5, 5, 5, 5",
            "snapOnInput": true,
            "startingDirectory": "%USERPROFILE%",
            "useAcrylic": true
        },
        {
            "acrylicOpacity": 0.59999999999999998,
            "closeOnExit": false,
            "colorScheme": "MaterialDark",
            "commandline": "Azure",
            "connectionType": "{d9fcfdfa-a479-412c-83b7-c5640e61cd62}",
            "cursorColor": "#FFFFFF",
            "cursorShape": "bar",
            "fontFace": "Consolas",
            "fontSize": 12,
            "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
            "historySize": 9001,
            "icon": "ms-appx:///ProfileIcons/{b453ae62-4e3d-5e58-b989-0a998ec441b8}.png",
            "name": "Azure Cloud Shell",
            "padding": "5, 5, 5, 5",
            "snapOnInput": true,
            "startingDirectory": "%USERPROFILE%",
            "useAcrylic": true
        },
        // gitbash配置
        {
            "acrylicOpacity": 0.75,
            "closeOnExit": true,
            "colorScheme": "MaterialDark",
            // bash位置
            "commandline": "C:\\Program Files\\Git\\bin\\bash.exe",
            "cursorColor": "#FFFFFF",
            "cursorShape": "bar",
            "fontFace": "Consolas",
            "fontSize": 12,
            "guid": "{1c4de342-38b7-51cf-b940-2309a097f589}",
            "historySize": 9001,
            // 图标
            "icon": "C:\\Users\\breeze\\Documents\\git.png",
            "name": "Bash",
            "padding": "5, 5, 5, 5",
            "snapOnInput": true,
            "startingDirectory": "./",
            "useAcrylic": true
        }
    ],
    // 终端配色
    "schemes": [
        {
            "name": "Breeze",
            "black": "#31363b",
            "red": "#ed1515",
            "green": "#11d116",
            "yellow": "#f67400",
            "blue": "#1d99f3",
            "purple": "#9b59b6",
            "cyan": "#1abc9c",
            "white": "#eff0f1",
            "brightBlack": "#7f8c8d",
            "brightRed": "#c0392b",
            "brightGreen": "#1cdc9a",
            "brightYellow": "#fdbc4b",
            "brightBlue": "#3daee9",
            "brightPurple": "#8e44ad",
            "brightCyan": "#16a085",
            "brightWhite": "#fcfcfc",
            "background": "#31363b",
            "foreground": "#eff0f1"
        },
        {
            "name": "Brogrammer",
            "black": "#1f1f1f",
            "red": "#f81118",
            "green": "#2dc55e",
            "yellow": "#ecba0f",
            "blue": "#2a84d2",
            "purple": "#4e5ab7",
            "cyan": "#1081d6",
            "white": "#d6dbe5",
            "brightBlack": "#d6dbe5",
            "brightRed": "#de352e",
            "brightGreen": "#1dd361",
            "brightYellow": "#f3bd09",
            "brightBlue": "#1081d6",
            "brightPurple": "#5350b9",
            "brightCyan": "#0f7ddb",
            "brightWhite": "#ffffff",
            "background": "#131313",
            "foreground": "#d6dbe5"
        },
        {
            "name": "Atom",
            "black": "#000000",
            "red": "#fd5ff1",
            "green": "#87c38a",
            "yellow": "#ffd7b1",
            "blue": "#85befd",
            "purple": "#b9b6fc",
            "cyan": "#85befd",
            "white": "#e0e0e0",
            "brightBlack": "#000000",
            "brightRed": "#fd5ff1",
            "brightGreen": "#94fa36",
            "brightYellow": "#f5ffa8",
            "brightBlue": "#96cbfe",
            "brightPurple": "#b9b6fc",
            "brightCyan": "#85befd",
            "brightWhite": "#e0e0e0",
            "background": "#161719",
            "foreground": "#c5c8c6"
        },
        {
            "name": "Github",
            "black": "#3e3e3e",
            "red": "#970b16",
            "green": "#07962a",
            "yellow": "#f8eec7",
            "blue": "#003e8a",
            "purple": "#e94691",
            "cyan": "#89d1ec",
            "white": "#ffffff",
            "brightBlack": "#666666",
            "brightRed": "#de0000",
            "brightGreen": "#87d5a2",
            "brightYellow": "#f1d007",
            "brightBlue": "#2e6cba",
            "brightPurple": "#ffa29f",
            "brightCyan": "#1cfafe",
            "brightWhite": "#ffffff",
            "background": "#f4f4f4",
            "foreground": "#3e3e3e"
        },
        {
            "name": "Material",
            "black": "#212121",
            "red": "#b7141f",
            "green": "#457b24",
            "yellow": "#f6981e",
            "blue": "#134eb2",
            "purple": "#560088",
            "cyan": "#0e717c",
            "white": "#efefef",
            "brightBlack": "#424242",
            "brightRed": "#e83b3f",
            "brightGreen": "#7aba3a",
            "brightYellow": "#ffea2e",
            "brightBlue": "#54a4f3",
            "brightPurple": "#aa4dbc",
            "brightCyan": "#26bbd1",
            "brightWhite": "#d9d9d9",
            "background": "#eaeaea",
            "foreground": "#232322"
        },
        {
            "name": "MaterialDark",
            "black": "#212121",
            "red": "#b7141f",
            "green": "#457b24",
            "yellow": "#f6981e",
            "blue": "#134eb2",
            "purple": "#560088",
            "cyan": "#0e717c",
            "white": "#efefef",
            "brightBlack": "#424242",
            "brightRed": "#e83b3f",
            "brightGreen": "#7aba3a",
            "brightYellow": "#ffea2e",
            "brightBlue": "#54a4f3",
            "brightPurple": "#aa4dbc",
            "brightCyan": "#26bbd1",
            "brightWhite": "#d9d9d9",
            "background": "#232322",
            "foreground": "#e5e5e5"
        },
        {
            "name": "MaterialOcean",
            "black": "#546e7a",
            "red": "#ff5370",
            "green": "#c3e88d",
            "yellow": "#ffcb6b",
            "blue": "#82aaff",
            "purple": "#c792ea",
            "cyan": "#89ddff",
            "white": "#ffffff",
            "brightBlack": "#546e7a",
            "brightRed": "#ff5370",
            "brightGreen": "#c3e88d",
            "brightYellow": "#ffcb6b",
            "brightBlue": "#82aaff",
            "brightPurple": "#c792ea",
            "brightCyan": "#89ddff",
            "brightWhite": "#ffffff",
            "background": "#0f111a",
            "foreground": "#8f93a2"
        },
        {
            "name": "idea",
            "black": "#adadad",
            "red": "#fc5256",
            "green": "#98b61c",
            "yellow": "#ccb444",
            "blue": "#437ee7",
            "purple": "#9d74b0",
            "cyan": "#248887",
            "white": "#181818",
            "brightBlack": "#ffffff",
            "brightRed": "#fc7072",
            "brightGreen": "#98b61c",
            "brightYellow": "#ffff0b",
            "brightBlue": "#6c9ced",
            "brightPurple": "#fc7eff",
            "brightCyan": "#248887",
            "brightWhite": "#181818",
            "background": "#202020",
            "foreground": "#adadad"
        }
    ]
}
```

终端配色可以到  [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/windowsterminal)  找

# 添加到右键菜单

图标 https://raw.githubusercontent.com/microsoft/terminal/master/res/terminal.ico 

新建一个.reg文件如： `addwt.reg` ，添加如下内容

```bash
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt]
@="Windows Terminal here"
"Icon"="%USERPROFILE%\\AppData\\Local\\Terminal\\terminal.ico"

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt\command]
@="%USERPROFILE%\\AppData\\Local\\Microsoft\\WindowsApps\\wt.exe"

```

Icon指向图标的位置

执行reg文件

修改terminal配置文件中的 `startingDirectory`改为：`./` 即：`"startingDirectory": "./"` 

删除对应的注册表就能删除右键菜单