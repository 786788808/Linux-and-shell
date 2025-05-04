[在线测试工具(临时用下)](https://c.runoob.com/compile/18/)  
参考文档，有更好的后续会update:  
[参考文档1](https://shellscript.readthedocs.io/zh_CN/latest/index.html)  
[参考文档2](https://www.gnu.org/software/bash/manual/bash.html)  
[参考文档3](http://manual.51yip.com/shell/)

### 1.什么是shell
shell，直译外壳，它是操作系统的外壳。我们可以通过shell命令来操作和控制操作系统。可理解成，Shell是一个命令解释器，它通过接受用户输入的Shell命令来启动、暂停、停止程序的运行或对计算机进行控制。  
说人话一点，可以把shell比喻成一个翻译官，我写了人类能看懂的脚本（ABCDEFG……），想要计算机去帮我干活，但是计算机它只懂机器语言（0101010101），在这种鸡同鸭讲的情况下，于是请来了shell来当翻译官，将人类的指令翻译成机器能识别的语言，然后让机器去干活。  
不过，我们常说的shell指的是shell script，而不是开发shell本身这意思。    
所有linux命令，可以直接在shell当中被调用。    
AND shell 区分大小写。  

### 2.shel的种类
Linux的Shell种类众多，常见的有：  
- Bourne Shell（/usr/bin/sh或/bin/sh）
- **Bourne Again Shell（/bin/bash）**
- C Shell（/usr/bin/csh）
- K Shell（/usr/bin/ksh）
- Shell for Root（/sbin/sh）  

它们由不同的人或组织、实验室研发出来（各有优缺点，详情请google），我们常用的就是 Bourne Again Shell，缩写: bash .它是linux标准的默认shell ，它基于Bourne shell，吸收了C shell和Korn shell的一些特性。bash完全兼容sh，也就是说，用sh写的脚本可以不加修改的在bash中执行。  
可通过以下命令查询自己的linux支持什么shell：cat ./etc/shells    
![image](https://user-images.githubusercontent.com/32427537/149654418-efd18470-1a82-4481-909f-de9330839140.png)     
可通过echo $SHELL查看默认shell: （这只是其中一种查看方式）     
![image](https://user-images.githubusercontent.com/32427537/149655156-a37babc9-ac44-41af-902e-0e8a4d3659f7.png)    

### 3.#!/bin/sh 表明解释器信息  
shell script第一行，常见：`#!/bin/sh` or `#!/bin/bash`,这一行被称为`shebang`行      
`#!` 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即这个脚本使用哪一种 shell。它会沿着给定的路径去找就是了。如果没有这一行，该程序可能会无法执行，因为系统可能无法判断该程序需要使用什么shell来执行（不懂的别纠结，学多几门语言就知道了）    
e.g.我们已经在hush1目录下，有test_hello_world.sh了:    
![image](https://user-images.githubusercontent.com/32427537/149659528-e47afc31-b373-4719-a83e-5eda944af7cb.png)    

我们想要执行这份shell script,有两种方式执行脚本。    
- 法1：./test_hello_world.sh  
- 法2：sh test_hello_world.sh  

![image](https://user-images.githubusercontent.com/32427537/149659714-96c6e627-936b-49c2-8192-3e735b6e14b1.png)  
法2sh，不需要在第一行指定解释器信息，写了也没用  

### 4.变量
变量命名规则：变量名称可由字母、数字和下划线组成，但是**不能以数字开头**。并且不能使用shell里面的关键字。  
在bash中，变量的默认类型是字符串类型。如果要进行数值运算，则必须指定变量类型为数值型。  

### 5.输入输出重定向
 | 设备      | 设备文件名     | 文件描述符     | 类型     |
| ---------- | :-----------:  | :-----------: | :-----------: |
| 键盘     | /dev/stdin     |  0     | 标准输入     |
| 显示器     | /dev/stdout     |  1     | 标准输出     |
| 显示器     | /dev/stderr     |  2     | 标准错误输出     |

因为设备文件名比较难记，就用文件描述符：0 1 2 分别来表示标准输入（键盘输入） 标准输出（输出到屏幕） 标准错误输出（输出到屏幕）    
 输出重定向：一般的输出是，我们输入命令后，在显示器显示输出结果，但是重定向，就是把命令的结果输出到指定的文件当中。

 | 类型      | 符号     | 作用     |
| ---------- | :-----------:  | :-----------: |
| 标准输出重定向     | 命令 > 文件     |  以**覆盖**的方式，把命令的正确输出输出到指定的文件或设备当中     | 
|      | 命令 >> 文件     |  以**追加**的方式，把命令的正确输出输出到指定的文件或设备当中     | 
| 标准错误输出重定向     | 错误命令 2> 文件     |  以**覆盖**的方式，把命令的正确输出输出到指定的文件或设备当中    | 
|      | 错误命令 2>> 文件     |  以**追加**的方式，把命令的正确输出输出到指定的文件或设备当中    | 
| 正确输出和错误输出同时保存    | 命令 > 文件 2>&1    |  以**覆盖**的方式，把正确输出和错误输出都保存到同一个文件中    | 
|    | 命令 >> 文件 2>&1    |  以**追加**的方式，把正确输出和错误输出都保存到同一个文件中    | 
|    | 命令 &> 文件     |  以**覆盖**的方式，把正确输出和错误输出都保存到同一个文件中    | 
|    | 命令 &>> 文件     |  以**追加**的方式，把正确输出和错误输出都保存到同一个文件中    | 
|    | 命令 >> 文件1 2>> 文件2     |  **分开储存输出结果**，把**正确的输出追加到文件1**中，把**错误的输出追加到文件2**中 |

常用的是同时保存正确输出和错误输出，并且以追加方式保存 还有最后一种分开储存正确、错误输出的一种类型。    
在shell脚本中，默认情况下，这三个文件处于打开状态     

`>`  默认为标准输出重定向，与 `1>` 相同  
`2>&1`  意思是把 标准错误输出 重定向到 标准输出.(这里的 `2` 和 `>` 之间不可以有空格，`2>` 是一体的时候才表示错误输出。)  

`&>file`  意思是把标准输出 和 标准错误输出 都重定向到文件file中  

/dev/null是一个文件，这个文件比较特殊，所有传给它的东西它都丢弃掉。当我们想执行命令，但又不想在屏幕看到相关信息，那就指到这个null文件，perfect…  
实操一下：    
把`stdout` 和`stderr` 分别存到不同的文件   
`find /home -name .bashrc > ./test_right 2> ./test_wrong`    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/bee2b3fb-5abd-4dd7-a630-3ab3577fa3e0)     
跟上面的对比一下,这里没有把标准错误输出写入文件，就会在屏幕显示出来        
`find /home -name .bashrc > ./test_right02`    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/c5543b24-ae85-4d9c-b542-2195279ba857)  
来看`/dev/null`,假设我只想看在屏幕上看到正确的信息，错误信息一律不想看，    
那就扔进黑洞里，`find /home -name .bashrc 2> /dev/null`，这里只有stdout, stderr被外星人带走不见了     
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/dbe37653-7c65-48b0-b0e6-5661f4b24c7b)  
再来另一个，`2>&1`，如果我想将stdout, stderr都写入同一个文件merge_log   
`find /home -name .bashrc > merge_log 2>&1`    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/a71b38d5-27d1-426c-b194-1f2f1bc689e1)     
`find /home -name .bashrc &> merge_log_02`    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/87d1c58c-59a4-41c9-b195-3e87d41bf649)   
上面的两种写法，二选一，不要写成`find /home -name .bashrc > merge_log 2> merge_log`，我劝你善良，记住上面的两个就好了     

### 6.多命令顺序执行
 | 多命令执行符      | 格式     | 作用     |
| ---------- | :-----------:  | :-----------: |
| ;     | 命令1 ; 命令2     |  多个命令顺序执行，命令之间没有任何逻辑联系     | 
|  &&    | 命令1 && 命令2     |  逻辑与，当命令1正确执行，则命令2才会执行；当命令1执行不正确，命令2也不会执行     | 
|  ||    | 命令1 || 命令2     |  逻辑或，当命令1正确执行，命令2不会执行；当命令1执行不正确，命令2才会执行     |

比如，关机前，我想先跑两次`sync`再跑`shutdown`, `sync; sync; shutdown -h now`, 前一个命令是否成功执行，与后一个命令是否要执行是无关的。不管死活类型。    
假设，我想判断/tmp/hush_dir 是否存在，如果存在就输出exist,不存在就输出not_exist  
`ls /tmp/hush_dir && echo "exist" || echo "not_exist"`  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/bac141cb-73ea-4287-8516-df72ded8abcf)  
记住`command1 && command2 || command3`,顺序通常不会变，command2 and command3 会使用肯定可以执行成功的命令  

### 7.注释
第一行的`#!/bin/sh`和这里的注释是不同的，它是一个特例  
单行注释，用经典的`#`开头  
多行注释，可以用多个`#`，也可以直接选用多行注释：    
`:<<EOF`
`注释内容... `   
`注释内容...  `  
`注释内容...  `  
`EOF`  
怎么理解多行注释呢？    
`:`冒号在Bash里也是一个命令，表示什么都不做，而`<<`是输入重定向，两个EOF(可用其它特殊成对字符替代)之间的内容通过<<追加给冒号（:），但是冒号对它们啥都不做，就相当于没做任何处理和输出，就相当于注释了

### 8.管道符
管道符`|`，` 命令1 | 命令2`，将命令1的**正确输出**作为命令2的操作对象    
e.g.:
`history | grep 'hush123'`  
`cat 'hush_file1' | rev | cut -d',' -f2 | rev`

### 9.通配符和其他特殊符号
这个学过其他语言很好理解    
`?`,匹配任意一个符号    
`*`,匹配0个或任意多个任意字符，也就是可以匹配任意内容      
`[]`,匹配中括号中任意一个字符。例如，[abc]代表一定匹配一个字符，或者a,或者b,或者c      
`[-]`,匹配中括号中任意一个字符，在一个范围内，常见有[a-z],[0-9]    
`[^]`,逻辑非，匹配不是中括号内的一个字符。例如：[^0-9]代表匹配一个不是数字的字符  
单引号里的
双引号


### 10.判断
10.1 按照文件类型进行判断：  
 | 测试选项      | 作用     |
| ---------- | :-----------:  |
| `-e`     | 判断文件是否存在，存在就为真     |
| `-d`     | 判断文件是否存在，并且是否为目录文件（是目录，则为真）     |
| `-f`    | 判断该文件是否为真，是否为普通文件（是普通文件，则为真）     |

两种判断格式：    
`test -e etl_job.log`,判断 etl_job.log 这个文件是否存在    
`[ -e etl_job.log ]`,判断 etl_job.log 这个文件是否存在(中括号两边一定要留空格)      
输出结果要用`$?`来看（上一条命令的执行结果），如果输出结果为0，就代表正确；输出结果非零，就代表错误  
by the way,这么写去判断是因为机器要拿来判断，不是我们人眼去ls,然后看文件是否存在，是什么文件类型     
示例：  
![image](https://user-images.githubusercontent.com/32427537/156007257-e8e67354-f33c-445e-aa9e-3af0000da1e2.png)  
![image](https://user-images.githubusercontent.com/32427537/156008312-167e366a-1a9c-4f45-b423-e1964a951708.png)  
![image](https://user-images.githubusercontent.com/32427537/156009088-3c62efdb-1508-4a1f-84d6-ba736a222354.png)    
  
10.2 按照文件的权限进行判断：  
 | 测试选项      | 作用     |
| ---------- | :-----------:  |
| `-r`     | 判断文件是否存在，并且是否拥有读权限（有读权限为真）     |
| `-w`     | 判断文件是否存在，并且是否拥有写权限（有写权限为真）     |
| `-x`    | 判断该文件是否存在，并且是否拥有执行权限（有执行权限为真）     |

But,这里的判断不分文件拥有者、所属组还是其他所有者，只要有一人有r，就会判定其拥有读权限，其他类推。如果要细致判断权限，则要写脚本去判定了。  
![image](https://user-images.githubusercontent.com/32427537/156021717-ee149314-b3ec-4908-bb19-68c36b24661a.png)

### 11.
`$#`: 表示传入的参数数量,such as:`sh hush_demo.sh batch01 tableAA vendorA`, 跟随三个参数，即返回3.  
`$@`: 表示传入的参数列表,such as:`sh hush_demo.sh batch01 tableAA vendorA`, 即返回batch01 tableAA vendorA  

`for var in $@:`    
`do`    
`    echo "$var"`  
`done`  

`$?`: 表示最后命令的退出状态，0表示没有错误，其他表示有错误   
`$0`: 表示要执行的shell脚本名称  
`$1` `$2` `$3`… `$n` 类推:  表示传入到脚本中对应位置的参数，第1个参数值，第2个参数值，第3个参数值… 第n个参数值，类推  
`$$`: 表示Shell本身的PID（ProcessID）  
`$!`: 表示Shell最后运行的后台Process的PID  

basename与dirname：    
`shell_dir=$(cd `dirname $0`; pwd)`  
其中，  
dirname $0，获取当前脚本所在绝对目录   
cd `dirname $0`，进入这个目录（切换当前工作目录）   
pwd，显示切换后脚本所在的工作目录  

### 12 数组(Array)
举个例子: `line_num=(11 22 33 44)`  `height=(163 168 180 "null_val")`  
数组是若干数据的集合，其中的每一份数据都称为元素(Element）。元素的下标从0开始。
赋值号两边不能有空格，数组名紧挨数组元素。常见的Bash Shell 仅支持一维数组，不支持多维数组。
shell 是弱类型语言，所以看到上面的height有数值也有字符串，有点类似python的list。
(1) 获取单个数组元素 ${array_name[index]}
`echo ${line_num[0]}`

(2) 输出所有数组元素
两种写法，任君选择
`echo ${line_num[@]}`
`echo ${height[*]}`

(3) 增加元素
`line_num[4]=55`
`echo ${line_num[*]}`

(4) 修改元素
`line_num[0]=555`
`echo ${line_num[*]}`

(5)稀疏数组
元素不一定是连续的
写法1：
`weight[0]=66`
`weight[5]=666`
`weight[10]=6666`
`echo ${weight[*]}`

写法2：
`ages=([3]=18 [5]=19 [10]=22)`
`echo ${ages[*]}`

### 13 环境变量
可用`env`, `export`, `set`查看  
- `HOME`:
- `SHELL`: 目前这个环境使用的SHELL使用的是哪个程序，Linux默认使用的是/bin/bash
- HISTSIZE`:
- `MAIL`:
- `PATH`: 执行文件查找的路径。目录与目录中间以冒号隔开，由于文件的查找是依序由PATH的变量内的目录来查询，所以目录的顺序也很重要  
- `LANG`:
- `RANDOM`:
- `PS1`: 命令提示字符的设置，这个有意思，平时我们输入命令的时候都会看到这些符号，但原来是这里去设置的，可以根据个人喜好去设置，并不是写死的  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/8cad7206-324e-4a0f-b700-55480ecd9d37)  
- `$`: 美元符号也是个变量，表示本SHELL的进程ID，即PID。可以 `echo $$`试试。  
- `?`: 这个就很常用啦，这个变量是上一个执行命令的返回值，0代表上一个命令成功执行，非0就是上一个命令执行失败
-  
### 14 read
实现与用户交互，可以读取来自键盘输入的变量，比如，我们经常可以看到输入Y,N这种case    
- `read 变量名`  
- `-p`,这个会有提示字符出现，用户用起来比较友好  
- `-t` ,比如接60，表示我给你60秒输入,超时不输入就以非零状态退出        
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/38eff00f-fe4b-4f52-b456-8506abf50a9a)  
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/dd330b0e-ce6f-43ea-8b9a-d87082156f43)  
如果用户超时不输入值，那么就自动退出了，手动再见啦~      
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/29fd466d-f766-4f6f-a3b7-525da2e26d14)  
- `-s`,令输入的数据不显示在终端上，输入密码常用。对比显示和隐藏两种case:  
无加密版：  
`#!/bin/bash`  
`# to test read command`  
`read -p 'please input your accout: ' user_account`  
`read -p 'please input your password: ' user_pw`  
加密版:  
`#!/bin/bash`  
`# to test read command`  
`read -p 'please input your accout: ' user_account`  
`read -s -p 'please input your password: ' user_pw`  
- `-n`, 设置输入的字符数
### 14.stty (setting tty终端)
帮助设置终端的输入按键代表的意义  
`stty -a`  
将目前的stty 参数列出来。一般也不会去改这些设置，可以记住一下`ctrl+s`,锁死界面，然后`ctrl+q`,解锁界面，可以玩玩~      
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/2969da9c-8a89-4de3-91b3-050a47b53738)

### 15.cut
直译，切割，处理信息是以行为单位的      
-d 表示以什么为分隔符     
-f 表示取第几个      
-c 表示以字符的单位取出固定字符区间    
假设我想把环境变量`PATH`,取第3个路径，那么可以`echo ${PATH} | cut -d ':' -f 3`,如果是去第1和第3个,还可以`echo ${PATH} | cut -d ':' -f 1,3`           
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/d4a969eb-4e2b-4871-8113-c699f9c0aaa0)        
下面示范一下-c的作用，借`export`来用一下，比如我想取得第12个字符以后的所有字符， `export | cut -c 12-`    
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/8061cf56-d384-4cb6-8730-73ef0b34d20f)      
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/450ee607-172c-4a5c-911b-629ddd1ab277)     

### 16.grep
分析一行数据，若当中有我们想要的信息，就将该行拿出来    
`grep [-acinv] [--color=auto] '查找字符' filename`   
-a:
-c: 计算找到'查找字符'的次数  
-i: 忽略大小写  
-n: 输出的同时显示行号  
-v: 反向选择，显示没有'查找字符'的那一行  
`last | grep 'hush' | less`    
`last | grep -v 'hush' | less`    
`last | grep -nv `hush'`  
`last | grep -vc 'hush'`   
`history | grep -i "VIM"`
`history | grep -in "VIM"`

### 17.sort
`sort [-fbMnrtuk] [file or stdin]`  
选项与参数：  
-f: 忽略大小写    
-b: 忽略最前面的空格字符  
-M:   
-n: 以数值来排序，默认的是字符串形式  
-r: 反向排序    
-u: uniq,相同的数据中，仅出现一行代表    
-t: 分隔符号，默认是 [Tab] 键    
-k: 选择以哪个 field 来进行排序  
`cat /etc/passwd | sort -t ':' -k 3`  
`cat /etc/passwd | sort -t ':' -k 3 -n`  
以':'为分隔符，取第三个field来做排序，只有加了`-n`,才会以数值来排序，不然按字符串来排序  


### 18 uniq
`unie [-ic]`   
选项与参数：  
-i: 忽略大小写    
-c: 计数     
`cut -d ' ' -f1 | sort | uniq`  
`last | cut -d ' ' -f1 | sort | uniq -c`   
![image](https://github.com/786788808/Linux-and-shell/assets/32427537/2e2ea618-eda4-4352-b3df-584936e46188)   

### 19 wc
- `wc -l`：查询行数，比如查询hush_demo.txt有多少行, `wc -l ./hush_demo.txt`  
- `wc -w`:
- `wc -m`:
  
### 20 tee 双重定向
同时将数据流分送到文件与屏幕(stdout)

### 21 tr
可以用来删除一段信息中的文字，或者进行文字信息的替换  

### 22 col
将[TAB]键替换成空格键  

### 23 join
处理两个文件中的数据，类似sql的join，相同值才会连在一起，但在这里，要注意排序，如果排序不同，导致同一行的数据值不同，压根不上，所以maybe you need sort first.  

### 24 paste
与jion不同，它不需要对比，是直接A file 的行数据拼接上B file的行数据，中间以[Tab]键隔开。  
- `paste fileA fileB`:  
- `paste -d ' ' fileA fileB`:  
  
### 25 expand
将[tab]键转换成空格键  

### 26 split
将文件拆分，可根据文件size ，也可根据行数去将一整份文件，拆成小文件。  

### 27 find
指定名字找文件 -name, 可以加上模糊匹配查找     
指定文件大小找文件 -size, 支持使用 + 或 - 表示大于或小于指定大小, 单位可以是 c（字节）、w（字数）、b（块数）、k（KB）、M（MB）或 G（GB）    
指定文件所有者查找 -user  
按文件类型查找 -type type, 可以是 f（普通文件）、d（目录）、l（符号链接）等   
还可以按照文件最后修改时间、文件被访问最后时间、状态发生过改变等等来查找  
`find /home/hush -name "*.txt"`, 找 /tmp 下文件所有者是 hush 的 txt 文件    
`find /tmp -user hush`, 找 /tmp 下文件所有者是 hush 的文件  
`find /tmp -size +2M`, 找 /tmp 下大于 2M 的文件    
`find /tmp -type d`, 找 /tmp 下的目录   

### 28 locate 定位文件所在位置
locate 基于预建数据库（如 /var/lib/mlocate/mlocate.db）快速匹配文件路径, 首先要更新背后的数据库,`updatedb` (要有权限才行)     
然后定位 file 位置, `locate aa.txt`       
![](https://s3.bmp.ovh/imgs/2025/05/01/f9316aa1d4f60ec6.png)    

### 29 which 定位二进制文件位置
查看指令"bash"的绝对路径，`which bash`   
查看指令"which"的绝对路径，`which which`    
![](https://s3.bmp.ovh/imgs/2025/05/01/5391a54b9c261d29.png)  

### 30 crontab 设置定时任务
`crontab -e`, 然后输入要设置的任务，比如`*/1 5 25 12 * echo `date` >> /tmp/test_crontab.txt`, 在每年 12 月 25 日凌晨 5 点的时候，每隔开 1 分钟，都会去输出 date 的 information 到 /tmp/test_crontab.txt 里面  
`crontab -l`, 查看有什么定时任务  
`crontab -r`, 把所有的定时任务都清掉   

### 31 at 一次性定时计划任务
使用 at 命令的时候，一定要保证 atd 进程的启动，执行`ps -ef | grep atd` 查询即可。下图看到有 atd 进程      
![](https://s3.bmp.ovh/imgs/2025/05/02/bfd4eb7d6870de69.png)   
比如，2 分钟之后要 ls 查看一下有什么文件，并把结果输出到 /tmp/tmp_at.txt, 执行 `at now + 2 minutes`, `ls > /tmp/tmp_at.txt`, 连续按`ctrl + d` 2 次退出  
![](https://s3.bmp.ovh/imgs/2025/05/02/6ba7ec66f73debe1.png)   
比如，2 天之后 5 点钟要查看一下 date 信息，并把结果输出到 /tmp/tmp_at2.txt, 执行 `at 5pm + 2 days`, `date > /tmp/tmp_at2.txt`, 连续按`ctrl + d` 2 次退出  
![](https://s3.bmp.ovh/imgs/2025/05/02/214b450d219b90b8.png)    
查看一下未来的任务 `atq`, 任务执行完，就不会出现在这个 list 里面
![](https://s3.bmp.ovh/imgs/2025/05/02/e481a2f47ac4903b.png)    
如果要删除这些定时任务，根据任务编号删除即可，比如我要删除编号为 5 的定时任务，删除它，执行`atrm 5`    
![](https://s3.bmp.ovh/imgs/2025/05/02/d5ef0ae7181c2a50.png)  
其他参数自行查，这里粗略带过

### 32 lsblk 查看所有设备挂载情况
`lsblk`  
![](https://s3.bmp.ovh/imgs/2025/05/02/c047cb887190c769.png)  
`lsblk -f`  
![](https://s3.bmp.ovh/imgs/2025/05/02/c5c00d572a1c3009.png)  

### 33 df -h 查询指定目录的磁盘占用情况
`df -h`, 查询系统整体磁盘使用情况  
![](https://s3.bmp.ovh/imgs/2025/05/03/3795eb091f86461b.png)

### 34 du -h 查询指定目录的磁盘占用情况
不添加目录，默认为查询当前目录的磁盘占用情况。添加目录，会去查询指定目录的磁盘占用情况       
`-s`,指定目录占用大小汇总    
`-h`,带计量单位，M G 等    
`-a`,含文件      
![](https://s3.bmp.ovh/imgs/2025/05/03/a508621b4f4b5876.png)    
`-max-depth=1`,子目录深度    
![](https://s3.bmp.ovh/imgs/2025/05/03/fd7cc02ad93e61bf.png)    
`-c`,列出明细的同时，增加汇总值    
![](https://s3.bmp.ovh/imgs/2025/05/03/36968320bb736b2f.png)    

### 35 统计特定目录下文件的个数
比如要统计 /tmp/tmp_custom/test 的文件数量，`ls -l /tmp/tmp_custom/test | grep "^-" | wc -l`     
![](https://s3.bmp.ovh/imgs/2025/05/03/ea6884c64599d628.png)      
![](https://s3.bmp.ovh/imgs/2025/05/03/6f6bbf51d5178bc9.png)    

### 36 统计特定目录下目录的个数
`ls -l /tmp/tmp_custom/test | grep "^d" | wc -l`  
![](https://s3.bmp.ovh/imgs/2025/05/03/4b80e6ef981764e1.png)    
`ls -l | grep "^d" | wc -l`     
![](https://s3.bmp.ovh/imgs/2025/05/03/27fbecedd229ec74.png)  

### 37 统计特定目录下文件的个数，包括子目录的
`ls -lR | grep "^-" | wc -l`  
![](https://s3.bmp.ovh/imgs/2025/05/03/14d86a854c9f0488.png)   

### 36 统计特定目录下目录的个数，包括子目录的
`ls -lR | grep "^d" | wc -l`  
![](https://s3.bmp.ovh/imgs/2025/05/03/ab799004467bf5f9.png)    

### 37 以树状显示目录结构
`tree ./`  
![image](https://imgur.la/images/2025/05/03/image40414ef28958d1da.png)  

### 38 增加一块硬盘
假设有 sda，现在加第 2 块
虚拟机添加硬盘   
分区 fdisk /dev/sdb  
![image](https://imgur.la/images/2025/05/03/imagef4d6e137e950f0cc.png)  
格式化  
![image](https://imgur.la/images/2025/05/03/image897afd6544337ae1.png)  
挂载（用命令行挂载后，重启后会失效）    
![image](https://imgur.la/images/2025/05/03/image9ae7d2d3c26ee9ae.png)  
设置永久挂载，修改 /etc/fstab，添加后，执行 `mount -a` 即刻生效    
`cat /etc/fstab`  
![image](https://imgur.la/images/2025/05/03/image32e2c9af48905f7e.png)  

### 39 NAT 网络配置
他人参考图： 
#### Linux 网络配置相关信息
![image](https://imgur.la/images/2025/05/03/image13a83430e60eb6fe.png)  
自身  
![](https://s3.bmp.ovh/imgs/2025/05/04/a6ae13057b24cae2.png)    
IP: 192.168.163.128, 为什么是 192.168.163 开头，可查编辑，虚拟网络编辑器配置    
![image](https://imgur.la/images/2025/05/04/imagec3a968c5b3139c46.png)      
NAT 设置：  
![image](https://imgur.la/images/2025/05/04/image42aa47867001f476.png)  
网关：192.168.163.2  
#### Windows 网络配置相关信息
CMD里`ipconfig` 查 IP：  
![image](https://imgur.la/images/2025/05/04/image184a4a17b4fd34b6.png)    
图形界面查看：  
![image](https://imgur.la/images/2025/05/04/image9da4e82087b94677.png)  
### 40 查看、修改 hostname
`hostname`  
![image](https://imgur.la/images/2025/05/04/image0b997f2d0ab69936.png)      
`vim /etc/hostname`, 修改完之后要 `reboot`  
![image](https://imgur.la/images/2025/05/04/image615bb26330d8db38.png)  
![image](https://imgur.la/images/2025/05/04/image31322d1c355fc247.png)     
![image](https://imgur.la/images/2025/05/04/imagea5c362d26041806f.png)    
重启过后，可以看到 `hostname` 的变化  
![image](https://imgur.la/images/2025/05/04/imagee3c08478eb4f49b8.png)  

### 41 获取 IP
#### 自动获取
![image](https://imgur.la/images/2025/05/04/image89ebab656f12b4f7.png)  
linux 启动后会自动获取 IP, 缺点是每次自动获取的 IP 地址可能不一样，服务器不可这样设置，需要固定 IP      
![](https://s3.bmp.ovh/imgs/2025/05/04/271c8b7199158c5d.png)  

#### 指定 IP
修改配置文件来固定 IP，编辑 `vim /etc/sysconfig/network-scripts/ifcfg-ens160`（网卡的配置文件​​）, 使得 IP 地址变为静态的   
打开文件，可看到定义网卡 ens160 的网络参数（如 IP 地址、子网掩码、网关等），控制其启动方式、协议支持等  
先备份，再修改，`cat /etc/sysconfig/network-scripts/ifcfg-ens160 > /etc/sysconfig/network-scripts/ifcfg-ens160_bak_20250504`  

现在查自己的 IP 为 192.168.163.128, 假设，现在要将 IP 设置为 192.168.200.130，   
BOOTPROTO=static, dhcp 就是自动分配，static 是固定 IP  
IPADDR=192.168.200.130  
GATEWAY=192.168.200.2  
DNS1=192.168.200.2, 保存    
![](https://s3.bmp.ovh/imgs/2025/05/04/a61cfec591b795c2.png)  
然后，回到 VMware， 编辑，虚拟网络编辑器配置    
将子网 IP 192.168.163.2  改成 192.168.200.2 
![](https://s3.bmp.ovh/imgs/2025/05/04/206e77b9efbb7832.png)  
NAT 设置里也要改  
![](https://s3.bmp.ovh/imgs/2025/05/04/dcf79d3917a07fa0.png)  
确定，确定  
这时候可以看到xshell 也退出来了   
![](https://s3.bmp.ovh/imgs/2025/05/04/df5b0e172c877cb8.png)   
然后需要重启网络服务或者重启系统生效    
`service network restart`、 `reboot`  
重启后再次查询 IP, 可以看到 IP 已经变成了 192.168.200.130：  
![](https://s3.bmp.ovh/imgs/2025/05/04/25df36bbaa5e59a4.png)      
再看 `ipconfig`, IP 也已经变成了 192.168.200.130:  
![image](https://imgur.la/images/2025/05/04/image5b0be2bfb4188eac.png)  
试下通信 `ping 192.168.200.130`:
![image](https://imgur.la/images/2025/05/04/imagefe5ab16977f9659d.png)  
看到是 OK 的  

### 42 设置主机名和 hosts 映射
需要去修改 hosts 文件，C:\Windows\System32\drivers\etc\hosts  
看到 ping IP 是成功的，但是 ping hostname 是失败的，需要配置
![](https://s3.bmp.ovh/imgs/2025/05/04/271c8b7199158c5d.png)    


