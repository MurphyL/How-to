## Windows技巧

## 重新安装 `Windows`

### 安装包管理器 `Chocolatey`


```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```


```powershell
choco upgrade chocolatey
```

### 安装常用工具包

```shell
choco install googlechrome
choco install chromium
choco install firefox
choco install 7zip.install

choco install vlc
choco install irfanview
choco install paint.net
choco install steam

choco install openssh
choco install curl
choco install wget
choco install everything

choco install notepadplusplus.install
choco install fiddler
choco install intellijidea-community

choco install pandoc
choco install nodejs-lts

choco install youtube-dl
choco install rufus
```