## Linux常用命令:bowtie:

----
- Linux 命令的基本格式：命令 [选项] [参数]  
（后面两个可选项的叫法可能不一样，注意就行）  
    - 选项可以用来调整命令的功能，令结果以一定的方式显示。  
    - 参数即命令要处理/作用的对象。  
    - 命令**区分大小写**
    - 选项有简洁版的：`ls -a`, 也有完整版的 `ls --all`, 但基本用简洁版，因为懒呀
    - 有的命令不一定遵守日常的命令格式，这里只是最普通的那种  
    
----
Linux 是一个树形的文件系统结构，第一层目录：/ ，根目录。  
在 Linux 中，**一切皆文件**。     
超级用户是`#`开头，普通用户是`$`开头m。  

----
- 快捷键介绍（实用得很，自己试试效果更佳）：:heart_eyes:  
    - Tab: 补全用 ，可实现命令或者是文件名的快速补全
    - ctrl+L or clear 命令: 清屏
    - ctrl+C: 中断正在执行的程序
    - Ctrl+D: 退出当前 Shell 命令行
    - ctrl+A: 移动光标到行首（移行首）
    - ctrl+E: 移动光标到行末（移行尾）
    - ctrl+U: 删除光标之前的所有字符（往左删）
    - ctel+K: 删除光标之后的所有字符（往右删）
    - ctrl+R: 搜索历史命令
    - Esc+B: 移动到当前单词的开头（移词头）
    - Esc+F: 移动到当前单词的结尾（移词尾）     
    - Ctrl+W: 针对当前词，删掉光标以前的字符；如果放到词的最后一位的再后一位的空格上，就相当于删掉一个单词（删单词）  
    - Ctrl+Y: 粘贴使用 Ctrl+W，Ctrl+U 和 Ctrl+K 快捷键擦除的文本
----

shell 有很多种，而你的Linux机有多少种可以使用的shells呢？  
直接`vi /etc/shells`，即可看到。而Linux 默认使用Bash       
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/833589d0-3f79-4334-b5ff-da534517968b)  
当前用户默认使用的是什么shell呢？    
直接`vi /etc/passwd`,找到你的account，对应最右侧的shell，即是答案      
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/f2310937-3847-43c0-886b-76e66d142036)  
每种shell的语法都不同，比如，我们没有设置变量`var1`,然后我们在bash里，直接 `echo ${var1}`,只会显示空值。But，如果在其他shell，会恭喜你，收获报错。注意。  

----


### 1. ls命令  
ls即list缩写  
可用选项：    
`ls -a` 列出目录所有文件，包含以.开始的隐藏文件    
`ls -A` 列出除.及..的其它文件    
`ls -r` 反序排列    
`ls -t` 以文件修改时间排序    
`ls -S` 以文件大小排序    
`ls -h` 以易读大小显示    
`ls -l` l,是 long 的缩写。会详细地显示文件的权限、所有者、文件大小等信息    
`ls -d` 不会显示目录下的所有项目，只会显示你想要找的文件的详细信息，比如：ls -ld /dev    
`ls -i` 类似于查身份证ID的操作    
e.g. `ls -lh`    
![](https://s3.bmp.ovh/imgs/2022/01/b308bdbd4b796563.png)    
可以从这里获取到很多信息：    
第一列第一个字符，如果是小写字母d，即目录；如果是-（短横杠），即文件。    

### 2. pwd命令
`pwd` 即 print workig directory，查看当前工作目录的绝对路径。  

### 3. cd 命令
切换目录，即 Change directory    
e.g.:  
- `cd /` ，跳转到根目录。
- `cd sub_dir`, 到下一层 sub_dir 里面去了(联合pwd命令感受一下。)
- `cd ~`,`cd`
    - cd ~ 是跳转到当前用户的家目录
    - 如果是 root 用户，cd ~ 相当于 cd /root
    - 如果是普通用户，cd ~ 相当于 cd /home/ 当前用户名
- cd ..，跳转到上一级目录

### 4. mkdir命令
mkdir 即 make directory, 用于创建目录。     
命令所在位置：/bin/mkdir    
可用选项：    
-m: 对新建目录设置存取权限，也可以用 chmod 命令设置;  
-p: 沿着路径创建文件夹。路径中的某些目录可能不存在，没关系，加了-p，命令会自动帮你创建这一路的路径。  

e.g.:   
1）在 tmp 目录下，新建目录，如果目录本身不存在，记得加 -p 选项，否则报错。`mkdir -p test20220109/aa`,      
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
- `rm -rf test4`，如果你真的确定要删除 test4 这个文件夹里的所有东西，那么就执行这个，**慎用rm -rf**。
- `rm -i *.log`，删除所有.log 结尾的文件，但是删除前会逐一询问你是否删除，即 inquiry。
- `rm -rf /`,就是删除了整个系统，那就**GG**了。  

### 7. rmdir 命令
命令所在路径:/bin/rmdir   
该命令比较鸡肋，只能**删除空的目录**，在实际应用里用得比较少  
e.g. 目录 a 里包含目录 b，如果直接 rmdir a,会报错，只有将子目录b删了，才能删a  
![](https://s3.bmp.ovh/imgs/2022/01/783afcc6fcde86c1.png)

### 8. mv命令  
可实现剪切，可实现改名   
e.g.    
（1)将a1.sh剪切到 /tmp 目录下， mv a1.sh /tmp    
![image](https://user-images.githubusercontent.com/32427537/148682627-a313ad35-61e0-4153-944d-e92c9d052b4a.png)    
(2)将 a2.sh 改名为 a2_new.sh,可以理解为从原目录移走到原目录  mv a2.sh a2_new.sh    
![image](https://user-images.githubusercontent.com/32427537/148683505-d6160d7b-b2e2-44b9-ac9e-54ae17b45c4c.png)

### 9. cp命令
copy的意思，可实现将一个目录或者文件复制到另一个目录，也可实现将多个目录、多个文件复制到另一个目录。    
不同用户用cp command出来的效果不一样，文件的权限及属性都因人而异，如果是复制给其他用户使用，要注意别人能不能用到。  
命令所在位置：/bin/cp      
常用选项说明:  
`-r`，递归将原目录或文件全部打包带走，**复制目录的时候一定要带上**，即使目录里没东西    
`-p`，在复制的同时，可将源目录或者文件的时间、用户权限等设置一并带走复制   
`-i`，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答 y 时目标文件将被覆盖  

还可以在复制的时候顺带改名，这里不详述，自行 google 答案  
命令参考：  
`cp -r 源路径1 目标路径`   
`cp 源路径1 源路径2 目标路径`    
e.g.     
(1)现 /home/hush1 目录下有 ori_01 和 ori_02 两个子目录，需要将其 copy 到 /tmp 目录下，见下图    
加选项-r,代表递归的意思（recursive），通俗点就是，将文件夹下的所有子文件夹和文件打包，送到新的文件夹那里去    
![image](https://user-images.githubusercontent.com/32427537/148677337-547ced71-6f0b-48da-9cad-6875bdc844bd.png)  
(2)加上-p，可以看到把时间和权限都一并复制过去 tmp 目录下了（**linux无文件创建时间，但是有最后操作时间，如果想要把原时间一并带走，一定要加-p参数**）  
![image](https://user-images.githubusercontent.com/32427537/148681243-d778c0e1-8739-4523-9123-f61736b5d62b.png)  

### 10. history命令
最简单的用法，就是拿来查看历史命令，看你之前敲了啥。直接输入 history。    
`history n`, 可以输出最后 n 条命令，包含history n这一条命令   
`history | head -5`,查看最前的 5 条命令  
`history | tail -5`,查看最后 5 条命令  
`!n`, 比如用完 history 命令后，想重新执行第 n 条命令，可!n,执行第n行命令（平时脚本的路径太长，可以用这个就很快，当然也可以）  
`!!` or `!-1` or ctrl+P,直接执行最后一行的命令（记住感叹号后面没有空格）    
export HISTTIMEFORMAT='%F %T'，可设置**当前窗口**的 history 输出命令的执行时间，如果想它一直都有执行时间显示，那么就必须到/etc/profile文件里，用vim去改啦  
`history -c`, 清除所有执行过的命令，最好不要乱动历史命令，否则会被组员打死    
![image](https://user-images.githubusercontent.com/32427537/150628851-fd969d1b-4e8b-4468-a9f4-4e11bdf040ef.png)
![image](https://user-images.githubusercontent.com/32427537/150628891-aa83272e-1f54-450e-a3ad-534afe1ef14d.png)   
还有很多功能，这里写这么多先  

### 11. cat (concatenate)
cat（concatenate）命令用于连接文件并打印到标准输出设备上,简单点，就是把文件的内容连续输出到屏幕上，如果是查看大文件，用其他command吧     
`cat [-AbEnTv]`
选项与参数：  
-A：相当于-vET的整合选项，可列出一些特殊字符而不是空白  
-b: 列出行号，空白行不会显示行号，会跳过，与`-n`不同
-E: 将结尾的换行符`$`显示出来（Windows的换行符是`M$`)      
-n: 打印出空白行，连空白行都会显示行号，与`-b`选项不同，拿个文件cat一下就知道了  
-T：将`[Tab]`键以`^I`显示出来  
-V：列出一些看不见的特殊字符  

`cat -A aaaa.txt`:   
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/2eb46666-6656-4a46-bf77-5af9037a4591)

### 12. more命令


### 13. less命令
相比上一条命令，less拥有更丰富的功能，不得不说一句：Less is more.  

### 14. head命令
head 命令可用于查看文件的开头部分的内容，常用选项-n,自定义显示的行数  
`head test01.log`, 默认显示开头 10 行的 log    
`head -n 100 test01.log`, 设置显示前 100 行的 log    

### 15. tail命令
tail, 尾巴，用于显示文件里的最尾部的内容，平时用来看动态log，看自己跑的job有没报错。      
参数说明：    
`-f`, 循环读取
`-n <行数>`, 显示文件的尾部 n 行内容或者从第 n 行开始到最后一行  
示例：  
`tail -f test01.log`, 动态查看 test01.log  
`tail test01.log`, 默认看最后 10 行的 log  
`tail -n 888 test01.log`, 查看最后 888 行的 log  
`tail -n -888 test01.log`, 查看最后 888 行的 log  
`tail -n +888 test01.log`, 查看第 888 行到最后一行的 log（就这个比较特殊一点，+号）    

### 16. chmod命令
change mode, 修改用户对文件或目录的权限，即读写执行的权力  
这里只简单记录一下数字版的，英文字母版的参考菜鸟 or else.  
首先，要有用户的概念和读写执行的概念：    
User（文件所有者）、Group（文件所有者所在组）、及 Other（所有其他用户）      
数字代表的权限：r=4，w=2，x=1    
![image](https://user-images.githubusercontent.com/32427537/152125246-c0dc287f-6eba-4fca-b1bd-d295f728cb9c.png)

可以单改一个文件或者目录，也可以改一个目录并且连带其下的所有目录及文件  

示例：  
（1）修改一个目录或者文件的权限，    
`chmod 765 aaaa.sh`,       
文件所有者的权限，7=4+2+1 ，即有读写执行的权限  
用户组的权限， 6=4+2+0 ，即有读写的权限  
其它用户的权限， 5=4+0+1 ，即有读和执行的权限

（2）修改一个目录或者文件的权限    
具体需求：修改 /tmp/C 这个目录的权限为 777，并且修改其目录下的目录及文件权限为 777，那就加选项 `-R`,**大写R**    
`chmod -R 777 /tmp/C`,      
![image](https://user-images.githubusercontent.com/32427537/152122675-62e3fada-2e7d-4791-9731-35d6e49cf0ff.png)  

在winscp里，操作更简单，直接勾选权限，爽的一匹:relieved:。  

### 17.chown
change owner, 用于设置文件所有者和文件关联组的命令  
chown **需要超级用户 root 的权限才能执行此命令**，就算是文件所有者去修改，也只会报错  
示例：  
现有文件 aa.txt,文件所有者为 hush1，hush1 出差了，想将剩下的脚本给 hush999 来完成  
首先，要增加 hush999 这个用户,`useradd hush999`,    
然后，`chown hush999 aa.txt`, 即可将 aa.txt 转交给 hush999 用户啦:smiling_imp:    
![image](https://user-images.githubusercontent.com/32427537/152285754-2fd25717-9b5b-4ae4-b7c3-78805bad9686.png)  

### 18. chgrp命令
change file group ownership, 用于改变文件或者目录的所属组。  
命令所在位置：/bin/chgrp  
语法：chgrp [用户组] [目录或者文件]  
语法与上面的 chown 类似   
示例：  
现有文件 aa.txt,文件所在组为 hush1，现想将组换成 hush_group,    
首先，要增加 hush_group 这个组，`groupadd hush_group`,    
然后，`chown hush999 aa.txt`, 即可将 aa.txt 转交给 hush999 用户啦:smiling_imp:   
![image](https://user-images.githubusercontent.com/32427537/152289489-e7f8ac07-751a-4f3f-8201-48ffe031ae96.png)

### 19. umask命令
`umask -S`, 显示创建的目录和文件的默认权限（以 rwx 的形式显示）     
`umask`, 以数字方式查看掩码,  
![image](https://user-images.githubusercontent.com/32427537/152300157-8dbf489f-6fc2-48db-8ea3-7964c7f8167f.png)
我的显示0022，第一个0暂时不管，关注后三位的：022  
默认权限要用 777-022=755，即 rwxrwxrwx-(----w--w-)=rwxr-xr-x(针对目录才是755，文件还要减去execute权限）    
一般也不会去修改默认的权限  
示例：    
现自建目录 E 和文件 eeee,    
![image](https://user-images.githubusercontent.com/32427537/152294286-a0412da6-8ff2-4eaa-bcaa-142d6fae180a.png)     
查询目录及文件默认的权限，`ls -ld E`, `ls -l eeee`,       
![image](https://user-images.githubusercontent.com/32427537/152294943-6ffc5bcd-0270-4d33-9ad2-4ac1f6f7ad4d.png)    
**touch一个文件，默认是不会有execute权限的，这点跟目录是不同的（想想病毒就知道why了）**

### 20. df命令
显示磁盘空间使用情况。获取硬盘被占用了多少空间，目前还剩下多少空间等信息，如果没有文件名被指定，则所有当前被挂载的文件系统的可用空间将被显示。默认情况下，磁盘空间将以 1KB 为单位进行显示，除非环境变量 POSIXLY_CORRECT 被指定，那样将以 512 字节为单位进行显示：
可用选项：  
`-a`, 全部文件系统列表    
`-h`, 以方便阅读的方式显示信息    
`-i`, 显示 inode 信息    
`-k`, 区块为 1024 字节    
`-l`, 只显示本地磁盘     
`-T`, 列出文件系统类型    

### 21. su
su 即 switch user，切换用户
`su root`,切换成超级用户，接着输入密码，就可以切换成功了  


### 22. find
### 23. file
可以查看某个文件的基本信息，是属于ASCII或是数据文件或是二进制文件，且其中有没有使用到动态链接库(share libary)等信息  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/4a3d2f04-e987-46b0-9ab5-6c21217534e1)


### 24. alias命令
直译，别名，这是用来给 linux 命令起别名的命令（为了方便（偷懒））。但也只针对当前窗口，如果要永久生效，必须去文件设置。       
`alias`, 可以看到哪些命令有别名，直接输入alias可看到自己机子默认设置了什么别名          
`alias 别名='原命令 -选项/参数'`, 自定义指令的别名       
`unalias 别名`, 删除别名    
永久别名设置：  
`vim /etc/profile`, 全局生效  
`vim ~/.bashrc`, 当前用户生效  
示例：   
（1）起 aa 作为 history 命令的别名：      
![image](https://user-images.githubusercontent.com/32427537/152096056-4050a0ee-4561-4e87-9e9c-4e163ab7ab88.png)      
（2）删除别名：    
![image](https://user-images.githubusercontent.com/32427537/152097239-60193fea-dec6-4139-ae09-5fd90954d11b.png)      


### 25. shutdown命令
用于关机或重启的命令。早期，只有 shutdown 命令在关机或重启之前会正确地中止进程及服务这个命令相对其他关机命令，所以一般就选这个。现在随着 linux 的发展，比如 reboot 命令也会正确地中止进程及服务，但是仍建议使用 shutdown 来关机和重启。选最保险的就是了。        
`shutdown -h now`, 立刻关机，自己的虚拟机可以试试，平时上班不要冲动      
`shutdown -r now`, 立刻重启    
`shutdown -h 10`, 10 分钟后关机    
`shutdown -r 08:30`, 指定具体时间重启  
一般人员也不会在生产中用到，毕竟是关机重启。    
![image](https://user-images.githubusercontent.com/32427537/152313946-ad669553-15cd-4dd0-b371-76745cf28f95.png)    
 另外，可以了解一下 halt, poweroff, init 0, reboot, init 6.  
 
### 26.runlevel
`runlevel`查看系统运行级别     
`cat /etc/inittab`  

### 27.logout
`logout`, 让用户退出系统  

### 28.ping
 `–c`, count 次数，也就是 ping 的次数  
 `-i`, interval, 连接间隔   
linux 下的 ping 和 windows 下的 ping 稍有区别, linux 下 ping 不会自动终止,需要按 ctrl+c 终止或者用参数 -c 指定要求完成的回应次数   
示例：  
`ping baidu.com`, ping 百度，如果连接上了，要手动终止 ctrl+c  
`ping -c 10 -i 1 baidu.com`, ping 10 次，间隔 1 秒   

### 29.last
列出目前与过去登入系统的用户信息。所有用户都具有执行权限。    
命令所在路径：/usr/bin/last   
![image](https://user-images.githubusercontent.com/32427537/152552327-e4164802-0ec5-4676-b49b-0fa469935409.png)   

### 30.lastlog命令
列出每个用户最后登录的信息或者特定用户的上次登录信息。  
`lastlog`, 列出所有用户的信息  
`lastlog -u 123`， 只列出用户123上次登录的信息  
![image](https://user-images.githubusercontent.com/32427537/152553904-821a5570-8b2e-4c44-9140-803ebad05c7b.png)   

### 31.nmuti命令


### 32.yum命令
`yum install httpd`  

### 33./etc/passwd用户信息文件
Linux系统是一个多用户多任务的分时操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。    
用户的账号一方面可以帮助系统管理员对使用系统的用户进行跟踪，并控制他们对系统资源的访问；另一方面也可以帮助用户组织文件，并为用户提供安全性保护。    
越是对服务器安全性要求高的服务器，越需要建立合理的用户权限等级制度和服务器操作规范。    
在windows里，右键 计算机 ，选择 管理，在本地用户和组里，可以直观看到有什么用户、什么组。但在linux中，主要是通过用户配置文件来查看和修改用户信息。    

`vim /etc/passwd`, 可查看用户相关信息(可直接`man 5 passwd`    
字段1：用户名称，注意规范（root不一定代表超级管理员，但是0一定代表超级管理员，可联想IP与域名）    
字段2：密码标志，早期是把密码放在这里，但是现在变了，有密码就用`x`表示，没密码就什么都没写。看密码要去另一个文件看（`/etc/shadow`,只有超级用户才能看)       
字段3：UID，相当于身份号，超级用户用0表示，伪用户占有一定号码（不过似乎版本不同占的不一样），普通用户，我现在用的是CentOS Linux release 7.9.2009 (Core)，就从1000开始     
**伪用户一定不要删，用于启动服务之类的，删了系统就崩了，不要动就是了**
字段4：GID（用户初始组ID），一个用户只有一个初始组，一般默认就跟用户名一样（可以改，但一般也不去改初始组，不推荐改）。可以有多个附加组，然后拥有这些附加组的权限。    
字段5：存放关于用户的说明信息、备注，比如是Hush用的还是Amy用的，有点comment的感觉     
字段6：用户的home目录，超级用户就/root,普通用户就类似/home/hush1    
字段7：shell解释器，可以尝试useradd一个新用户，然后写一个错的shell路径，就可以登陆不进去了  
![image](https://user-images.githubusercontent.com/32427537/152649425-b61f25e0-44e0-4fcf-94c1-0f95afa4566f.png)

### 34./etc/shadow影子文件
可以看到密码，所以要保护好，不要外泄  
可以设置多久修改一次密码、看到上一次修改密码的时间、伪用户没密码（用\*或者！！表示）   
`cat /etc/shadow`    
`man 5 shadow`, 可以看到每个字段的作用      

### 35./etc/group组信息文件
`cat /etc/group`  
`man 5 group`,  
![image](https://user-images.githubusercontent.com/32427537/152651046-2c028b03-0016-43a9-bae9-44137b89a212.png)

### 36./etc/gshadow组密码文件


### 37.man
`man ifconfig`,  
`man ls`,   

### 38.useradd
添加新用户，也可以通过定义选项，手工去添加用户（用非默认的用户信息）    
`useradd hush2`, 新增加hush2用户  

### 39.passwd
设置用户密码  
`passwd hush1`, 设置 hush1 用户的密码, enter后输入新密码（超级用户方式）  
普通用户就直接`passwd`    

### 40.usermod
修改用户账号，更改用户的有关属性，如用户号、主目录、用户组、登录Shell等    
针对已有的账户，上面的useradd是针对新用户  

### 41.userdel
删除用户，也可通过手动删除相关文件内容来删除某个用户，但是比较麻烦，看需求选        
`userdel -r hush1`, 删除hush1用户，并且把家目录删掉，一般都带`-r`选项这样删才干净         

### 42.ID
`id hush1`, 查看hush1的ID号     
![image](https://user-images.githubusercontent.com/32427537/152673789-c80f201e-6f5c-42a1-98e0-6e7dad693a97.png)     

### 43.whoami
用于显示自身用户名称    
`whoami`,    
![image](https://user-images.githubusercontent.com/32427537/152673842-83c23a5c-3920-4ab6-9da0-975b71192dff.png)  
看到这命令不自觉想笑，啊哈哈哈哈

### 44.su
切换用户, switch user。如果超级用户切换成其他用户，不用敲密码，但若是其他用户进行切换，就要敲密码    
以前一直直接用`su`去切换用户，最近再看视频教程的时候，发现，最好还是用`su -`吧，把环境变量也改了，不然可能带来一定问题    
直接`su`的话，再用`env`查看环境变量，  
![image](https://user-images.githubusercontent.com/32427537/152674342-bd2cfb50-e63f-49dc-a14a-efb432eb4c85.png)  
如果`su -`的话，再用`env`查看环境变量，就是另一种景象（try try）   

### 45.screen

### 46.tmux

### 47.type（联动which)
查询命令是否为builtin command, `type [-tpa] name`  
`type ls`    
不加任何参数时，会显示出要查询的命令为外部命令还是bash内置命令    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/33c254b8-2a82-4280-a835-571be8b74e0d)    
`type -a ls`   
会由PATH变量定义的路径中，将所有含name的命令都列出来，参考此例子  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/bc0b32e9-4a3e-4c5a-823b-2856b9810514)    
`type -t ls`   
`type -t history`  
type -t会显示三种结果:  
file：表示command为外部命令  
alias:表示该命令为命令别名所设置的名称，比如`ls`  
builtin:表示该命令为bash内置的命令  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/362c2b8b-1111-4a83-9e6a-956dcd2ccbdd)   

### 48. which
e.g.:  
- which ls 
- which which










