## Linux常用命令

----
Linux命令的基本格式：命令 [选项] [参数]（后面两个可选项的叫法可能不一样，注意就行）  
- 选项可以用来调整命令的功能，令结果以一定的方式显示。  
- 参数即命令要处理/作用的对象。  
- 命令**区分大小写**
- 选项有简洁版的：ls -a,也有完整版的 ls --all,但基本用简洁版，因为懒呀
- 有的命令不一定遵守日常的命令格式，这里只是最普通的那种  
----

Linux是一个树形的文件系统结构，第一层目录：/ ，根目录。  
在Linux中，**一切皆文件**。     

----
快捷键介绍（实用得很）：  
- Tab: 补全用 ，可实现命令或者是文件名的快速补全
- ctrl+L or clear命令：清屏
- ctrl+C:中断正在执行的程序
- ctrl+A:移动光标到行首
- ctrl+E:移动光标到行末
- ctrl+U:删除光标之前的所有字符（往左删）
- ctel+K:删除光标之后的所有字符（往右删）
- 



### 1. ls命令  
ls即list缩写  
可用选项：    
`ls -a` 列出目录所有文件，包含以.开始的隐藏文件    
`ls -A` 列出除.及..的其它文件    
`ls -r` 反序排列    
`ls -t` 以文件修改时间排序    
`ls -S` 以文件大小排序    
`ls -h` 以易读大小显示    
`ls -l` l,是long的缩写。会详细地显示文件的权限、所有者、文件大小等信息    
`ls -d` 不会显示目录下的所有项目，只会显示你想要找的文件的详细信息，比如：ls -ld /dev    
`ls -i` 类似于查身份证ID的操作    
e.g. `ls -lh`    
![](https://s3.bmp.ovh/imgs/2022/01/b308bdbd4b796563.png)    
可以从这里获取到很多信息：    
第一列第一个字符，如果是小写字母d，即目录（文件夹）；如果是-（短横杠），即文件。    

### 2. pwd命令
`pwd` 即 print workig directory，查看当前工作目录的绝对路径。  

### 3. cd 命令
切换目录，即 Change directory    
e.g.:  
- `cd /` ，跳转到根目录。
- `cd sub_dir`, 到下一层sub_dir里面去了(联合pwd命令感受一下。)
- `cd ~`
    - cd ~ 是跳转到当前用户的家目录
    - 如果是root用户，cd ~ 相当于 cd /root
    - 如果是普通用户，cd ~ 相当于cd /home/当前用户名
- cd ..，跳转到上一级目录

### 4. mkdir命令
mkdir 即 make directory, 用于创建目录（or文件夹）。     
命令所在位置：/bin/mkdir    
可用选项：    
-m: 对新建目录设置存取权限，也可以用 chmod 命令设置;  
-p: 沿着路径创建文件夹。路径中的某些目录可能不存在，没关系，加了-p，命令会自动帮你创建这一路的路径。  

e.g.:   
1）在tmp目录下，新建目录，如果目录本身不存在，记得加 -p 选项，否则报错      
![](https://s3.bmp.ovh/imgs/2022/01/87b584d0c6cb6328.png)      
2）同时创建多个目录，要在bin目录下创建test目录，而test目录还包含test01和test02目录，注意他们都是原先不存在的目录     
Don't worry, Linux可以帮你做到      
![](https://s3.bmp.ovh/imgs/2022/01/ea8948ebd92f6985.png)    


### 5. touch命令
touch，可用于创建新文件(创建单个或同时创建多个)，也可用于  

e.g.:
- `touch y1.txt`，创建 y1.txt
- `touch y2.txt y3.txt y4.txt`，同时创建y2.txt, y3.txt, y4.txt
-

### 6. rm命令
rm 即 remove， 用于删除目录或者目录里的文件  
可用选项：  
-i： 删除前逐一询问确认    
-f： 即使原档案属性设为唯读，亦直接删除，无需逐一确认，简单点就是强制删的意思    
-r： 将目录及以下之档案亦逐一删除    

e.g.:  
- `rm test4`，这里的test4为一目录(文件夹)，无法直接删除，报错：rm: cannot remove 'test4': Is a directory。
- `rm -rf test4`，如果你真的确定要删除test4这个文件夹里的所有东西，那么就执行这个，**慎用rm -rf**。
- `rm -i *.log`，删除所有.log结尾的文件，但是删除前会逐一询问你是否删除，即inquiry。
- `rm -rf /`,就是删除了整个系统，那就**GG**了。  

### 7. rmdir 命令
命令所在路径:/bin/rmdir   
该命令比较鸡肋，只能**删除空的目录**，在实际应用里用得比较少  
e.g. 目录a里包含目录b，如果直接rmdir a,会报错，只有将子目录b删了，才能删a  
![](https://s3.bmp.ovh/imgs/2022/01/783afcc6fcde86c1.png)

### 8. mv命令  
可实现剪切，可实现改名   
e.g.    
（1)将a1.sh剪切到/tmp目录下， mv a1.sh /tmp    
![image](https://user-images.githubusercontent.com/32427537/148682627-a313ad35-61e0-4153-944d-e92c9d052b4a.png)    
(2)将a2.sh改名为a2_new.sh,可以理解为从原目录移走到原目录  mv a2.sh a2_new.sh    
![image](https://user-images.githubusercontent.com/32427537/148683505-d6160d7b-b2e2-44b9-ac9e-54ae17b45c4c.png)



### 9. cp命令
copy的意思，可实现将一个目录或者文件复制到另一个目录，也可实现将多个目录、多个文件复制到另一个目录。    
命令所在位置：/bin/cp      
常用选项有:  
-r，递归将原目录或文件全部打包带走，复制目录的时候一定要带上，即使目录里没东西    
-p，在复制的同时，可将源目录或者文件的时间、用户权限等设置一并带走复制   
还可以在复制的时候顺带改名，这里不详述，自行google答案

e.g.   
(1)现/home/hush1目录下有ori_01和ori_02两个子目录，需要将其copy到/tmp目录下，见下图    
加选项-r,代表递归的意思（recursive），通俗点就是，将文件夹下的所有子文件夹和文件打包，送到新的文件夹那里去    
![image](https://user-images.githubusercontent.com/32427537/148677337-547ced71-6f0b-48da-9cad-6875bdc844bd.png)  
(2)加上-p，可以看到把时间和权限都一并复制过去 tmp 目录下了（**linux无文件创建时间，但是有最后操作时间，如果想要把原时间一并带走，一定要加-p参数**）  
![image](https://user-images.githubusercontent.com/32427537/148681243-d778c0e1-8739-4523-9123-f61736b5d62b.png)  



### 10. history命令
最简单的用法，就是拿来查看历史命令，看你之前敲了啥。直接输入history。    
`history n`, 可以输出最后n条命令，包含history n这一条命令   
`history | head -5`,查看最前的5条命令  
`history | tail -5`,查看最后5条命令  
`!n`, 比如用完history命令后，想重新执行第n条命令，可!n,执行第n行命令（平时脚本的路径太长，可以用这个就很快，当然也可以）  
`!!` or `!-1` or ctrl+P,直接执行最后一行的命令（记住感叹号后面没有空格）    
export HISTTIMEFORMAT='%F %T'，可设置**当前窗口**的 history 输出命令的执行时间，如果想它一直都有执行时间显示，那么就必须到/etc/profile文件里，用vim去改啦  
`history -c`, 清除所有执行过的命令，最好不要乱动历史命令，否则会被组员打死    
![image](https://user-images.githubusercontent.com/32427537/150628851-fd969d1b-4e8b-4468-a9f4-4e11bdf040ef.png)
![image](https://user-images.githubusercontent.com/32427537/150628891-aa83272e-1f54-450e-a3ad-534afe1ef14d.png)   
还有很多功能，这里写这么多先  

### 11. cat命令
### 12. more命令
### 13. less命令
相比上一条命令，less拥有更丰富的功能，不得不说一句：Less is more.  

### 14. head命令
### 15. tail命令
### 16. chmod命令
### 17. df命令
显示磁盘空间使用情况。获取硬盘被占用了多少空间，目前还剩下多少空间等信息，如果没有文件名被指定，则所有当前被挂载的文件系统的可用空间将被显示。默认情况下，磁盘空间将以 1KB 为单位进行显示，除非环境变量 POSIXLY_CORRECT 被指定，那样将以512字节为单位进行显示：
可用选项：  
- -a 全部文件系统列表  
- -h 以方便阅读的方式显示信息  
- -i 显示inode信息  
- -k 区块为1024字节  
- -l 只显示本地磁盘   
- -T 列出文件系统类型  
### 18. su命令
su 即 switch user，切换用户
### 19. find命令
### 20. which命令
e.g.:  
- which ls 
- which which

### 21. alias命令
直译，别名。  
`alias`,可以看到哪些命令有别名。    
比如我自己的机子，默认的设置有：`ll`，相当于`ls -l`了；`vi` 相当于`vim`。    
![image](https://user-images.githubusercontent.com/32427537/150629377-c7fbffc7-efb6-4b49-9084-ece9601d3cc7.png)  


