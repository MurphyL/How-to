# 安装Windows之后的操作

安装`Chrome`：

> 下载链接： https://www.google.com/intl/zh-CN/chrome/


移出资源管理器中的`3D Object`库：

```cmd
  @echo off
  REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
  REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
  exit
```
