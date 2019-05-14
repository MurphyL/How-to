---
description: 安装Windows之后的操作
---

# Windows

安装`Chrome`替换`Edge`：

> 下载链接： [https://www.google.com/intl/zh-CN/chrome/](https://www.google.com/intl/zh-CN/chrome/)

安装`Notepad++`替换`Notepad`：

> 下载链接： [https://notepad-plus-plus.org/](https://notepad-plus-plus.org/)

安装`InfanView`替换`Photo`应用：

> 下载链接： [https://www.irfanview.com/](https://www.irfanview.com/)

移出资源管理器中的`3D Object`库：

```text
@echo off
REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
exit
```

## 其他

Office365 [https://portal.office.com/](https://portal.office.com/)

