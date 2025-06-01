

### 列出所有已安装的 Linux 发行版及其详细状态信息​
打开 Powershell, 输入 `wsl -l -v`  
![](https://s3.bmp.ovh/imgs/2025/06/01/cd65203be5e49e38.png)  

### 显示官方支持的 Linux 发行版名称  
打开 Powershell, 输入 `wsl --list --online`  
![](https://s3.bmp.ovh/imgs/2025/06/01/b3d34f461c442905.png)  

### 指定默认启动的 Linux 发行版
当系统中安装了多个 WSL 发行版（如 Ubuntu 22.04、Debian、Kali 等）时，此命令会强制将 Ubuntu-24.04 设为默认选项。此后在 PowerShell 或 CMD 中直接输入 wsl 命令（不带参数），系统会自动启动 Ubuntu 24.04 环境。提升操作效率。  
打开 Powershell, 输入 `wsl --set-default Ubuntu-24.04`  
`wsl -l -v` 行首的 * 表示默认发行版  
![](https://s3.bmp.ovh/imgs/2025/06/01/cd65203be5e49e38.png)   

### 在子系统中，用 Windows 记事本打开 linux 文件
`notepad.exe demo.txt`  
![](https://s3.bmp.ovh/imgs/2025/06/01/d62601d2be0bf8c2.png)  
### 在 Windows 里调用 linux 命令
打开 Powershell, 输入 `Get-ChildItem` 能获取当前文件夹的所有内容。利用 linux 的 `grep` 对输出结果进行过滤，输入 `Get-ChildItem | wsl grep Py`  
![](https://s3.bmp.ovh/imgs/2025/06/01/383ef763d7592ae0.png)  
![](https://s3.bmp.ovh/imgs/2025/06/01/c6bf1ff4743df44c.png)  

### 显卡直通
`sudo apt install nvidia-utils-535`  
`nvidia-smi`    
![](https://s3.bmp.ovh/imgs/2025/06/01/5e10195302c7cc50.png)  

