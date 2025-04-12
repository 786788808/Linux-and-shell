## 打开环境变量配置界面
rundll32 sysdm.cpl,EditEnvironmentVariables  
systempropertiesadvanced  
control sysdm.cpl,,3  
## 查看历史命令
doskey /history  
## 清屏
cls
## 显示Windows version
ver
## check IP
ipconfig       # 显示本机 IP  
ipconfig /all  # 显示详细网络信息  
## 切换目录
D:                 # 先进入 D 盘（仓库）  
cd Coding\Software # 再进入仓库里的房间（目录）  
cd /d D:\Coding\Software  # 直接坐电梯到 D 盘仓库的指定房间  
cd .. 回到上一级目录  
## list 
dir          # 列出当前目录 and 文件  
dir /s       # 递归列出子目录文件  
dir /A:D     # 仅显示当前目录的直系子目录（不递归）  
dir /A:D /B  # 仅显示目录名  
## 创建新目录 
mkdir NewFolder      # 创建文件夹  

