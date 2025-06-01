### 列出所有已安装的 Linux 发行版及其详细状态信息​
打开 Powershell, input `wsl -l -v`  
![](https://s3.bmp.ovh/imgs/2025/06/01/cd65203be5e49e38.png)  

### 启动子系统 Ubuntu-24.04
打开 Powershell, input `wsl -d Ubuntu-24.04`  
![](https://s3.bmp.ovh/imgs/2025/06/01/858ac7d393bd05c9.png)  
默认用户是root，不建议  

### 修改默认登录用户为普通用户
首先，确保有一个普通用户  
`adduser hush`     
`usermod -aG sudo hush`  # 授予sudo权限    
然后，修改 wsl.conf 文件  
`sudo nano /etc/wsl.conf`    
（​​wsl.conf 是针对单个 Linux 发行版，位于 Linux 子系统内​。​.wslconfig 是针对所有 WSL2 发行版,位于 C:\Users\<用户名>\.wslconfig，需要自己创建。若同一配置项在两者中冲突，​​wsl.conf 的本地设置优先级更高​​​​)
设定默认的user name  
`[user]`    
`default = hush`  
​​保存并退出编辑器​​：Ctrl+O → Enter → Ctrl+X（nano 编辑器）  
打开 Powershell, input    
`wsl --terminate Ubuntu-24.04`  # 终止实例  
`wsl -d Ubuntu-24.04`          # 重新启动    
![](https://s3.bmp.ovh/imgs/2025/06/01/fb7d2b465da732b1.png)

### 指定默认启动的 Linux 发行版
当系统中安装了多个 WSL 发行版（如 Ubuntu 22.04、Debian、Kali 等）时，此命令会强制将 Ubuntu-24.04 设为默认选项。此后在 PowerShell 或 CMD 中直接输入 wsl 命令（不带参数），系统会自动启动 Ubuntu 24.04 环境。提升操作效率。  
打开 Powershell, input `wsl --set-default Ubuntu-24.04`  
`wsl -l -v` 行首的 * 表示默认发行版  
![](https://s3.bmp.ovh/imgs/2025/06/01/cd65203be5e49e38.png)   

### 显示官方支持的 Linux 发行版名称  
打开 Powershell, input `wsl --list --online`  
![](https://s3.bmp.ovh/imgs/2025/06/01/b3d34f461c442905.png)  

### 在子系统中，用 Windows 记事本打开 linux 文件
input `notepad.exe demo.txt`  
![](https://s3.bmp.ovh/imgs/2025/06/01/d62601d2be0bf8c2.png)  

### 在子系统中，启动 Windows 资源管理器  
input `explorer.exe .`
打开资源管理器并定位到：​​\\wsl.localhost\Ubuntu-24.04\home\hush  
![](https://s3.bmp.ovh/imgs/2025/06/01/c260c95a43ceab2f.png)

### 在 Windows 里调用 linux 命令
打开 Powershell, input `Get-ChildItem` 能获取当前文件夹的所有内容。利用 linux 的 `grep` 对输出结果进行过滤，输入 `Get-ChildItem | wsl grep Py`  
![](https://s3.bmp.ovh/imgs/2025/06/01/383ef763d7592ae0.png)  
![](https://s3.bmp.ovh/imgs/2025/06/01/c6bf1ff4743df44c.png)  

### 显卡直通
`sudo apt install nvidia-utils-535`  
`nvidia-smi`    
![](https://s3.bmp.ovh/imgs/2025/06/01/5e10195302c7cc50.png)  

