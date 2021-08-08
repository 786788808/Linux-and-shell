## Linux常用命令
背景：  
Linux 渣渣表示要好好学点命令，才能好好装B。    
![](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Finews.gtimg.com%2Fnewsapp_match%2F0%2F12070489956%2F0.jpg&refer=http%3A%2F%2Finews.gtimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1631009983&t=ac346acc55d7a0dfaf99bbb1223d46f3)  
Linux是一个树形的文件系统结构，第一层目录：/ 。  
在Linux中，一切皆文件。
Linux命令格式：  
命令 [选项] [参数]  

#### 1. ls命令
ls即list缩写  
可用选项：  
ls -a 列出目录所有文件，包含以.开始的隐藏文件  
ls -A 列出除.及..的其它文件  
ls -r 反序排列  
ls -t 以文件修改时间排序  
ls -S 以文件大小排序  
ls -h 以易读大小显示  
ls -l 除了文件名之外，还将文件的权限、所有者、文件大小等信息详细列出来  

这个还是自己去敲出来比较容易记忆(其实我懒得截图)


#### 2. pwd命令
pwd 即 print workig directory，查看当前工作目录的绝对路径。

#### 3. cd 命令
cd 即 Change directory，切换目录  
e.g.:  
- cd / ，跳转到根目录。
- cd sub_dir, 到下一层sub_dir里面去了(联合pwd命令感受一下。)
- cd ~
    - cd ~ 是跳转到当前用户的家目录
    - 如果是root用户，cd ~ 相当于 cd /root
    - 如果是普通用户，cd ~ 相当于cd /home/当前用户名
- cd ..，跳转到上一级目录

#### 4. mkdir命令
mkdir 即 make directory, 用于创建文件夹。  
可用选项：  
-m: 对新建目录设置存取权限，也可以用 chmod 命令设置;
-p: 沿着路径创建文件夹。路径中的某些目录可能不存在，没关系，加了-p，命令会自动帮你创建这一路的路径。

e.g.:
- mkdir dir_1，创建一个叫 dir_1 的文件夹  
- mkdir test/test_1/test_2  
假设我现在在 /c/Users/Administrator/Desktop/git_test 下，我想要创建一个全新的 test 文件夹下的 test_1下的 test_2 文件夹（原本不存在test、test_1、test_2）

#### 5. touch命令
touch，可用于创建新文件(创建单个或同时创建多个)，也可用于  

e.g.:
- touch y1.txt，创建 y1.txt
- touch y2.txt y3.txt y4.txt，同时创建y2.txt, y3.txt, y4.txt
-

#### 6. rm命令
rm 即 remove， 用于删除目录或者目录里的文件  
可用选项：  
-i： 删除前逐一询问确认    
-f： 即使原档案属性设为唯读，亦直接删除，无需逐一确认，简单点就是强制删的意思    
-r： 将目录及以下之档案亦逐一删除    

e.g.:  
- rm test4，这里的test4为一目录(文件夹)，无法直接删除，报错：rm: cannot remove 'test4': Is a directory。
- rm -rf test4，如果你真的确定要删除test4这个文件夹里的所有东西，那么就执行这个，**慎用rm -rf**。
- rm -i *.log，删除所有.log结尾的文件，但是删除前会逐一询问你是否删除，即inquiry。

#### 7. rmdir 命令
该命令比较鸡肋，只能删除空的文件夹，暂时不管  

#### 8. mv命令

#### 9. cp命令

#### 10. history命令
查看历史命令，看你之前敲了啥。  
#### 11. cat命令
#### 12. more命令
#### 13. less命令
#### 14. head命令
#### 15. tail命令
#### 16. chmod命令
#### 17. df命令
显示磁盘空间使用情况。获取硬盘被占用了多少空间，目前还剩下多少空间等信息，如果没有文件名被指定，则所有当前被挂载的文件系统的可用空间将被显示。默认情况下，磁盘空间将以 1KB 为单位进行显示，除非环境变量 POSIXLY_CORRECT 被指定，那样将以512字节为单位进行显示：
可用选项：
-a 全部文件系统列表
-h 以方便阅读的方式显示信息
-i 显示inode信息
-k 区块为1024字节
-l 只显示本地磁盘
-T 列出文件系统类型
#### 18. su命令
su 即 switch user，切换用户
#### 19. find命令
#### 20. which命令
e.g.:  
- which ls 
- which which
