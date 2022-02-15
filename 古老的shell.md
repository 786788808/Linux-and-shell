工作中常用到shell script实现调用，记录一下          
### 1.什么是shell
刚开始接触shell的时候，只知道shell脚本扩展名为 sh，其脚本还带有linux命令……脚本读起来有点困难，一脸问号   
慢慢……知道了一点东西  
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
shell script第一行，常见：**#!/bin/sh** or **#!/bin/bash**    
#! 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即使用哪一种 Shell。沿着给定的路径去找就是了。（不懂的别纠结，学多几门语言就知道了）    
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

 | 设备 | 设备文件名 | 文件描述符 | 类型 |  
 | ---- | ---- | ---- | ---- | ---- |    
 | 键盘 | /dev/stdin | 0 | 标准输入 |  
 | 显示器 | /dev/stdout | 1 | 标准输出 |  
 | 显示器 | /dev/stderr | 2 | 标准错误输出 |  
 因为设备文件名比较难记，就用0 1 2 分别来表示标准输入 标准输出 标准错误输出    
 输出重定向：一般的输出是，我们输入命令后，在显示器显示输出结果，但是重定向，就是把命令的结果输出到指定的文件当中。  
 
 | 表格      | 第一列     | 第二列     |
| ---------- | :-----------:  | :-----------: |
| 第一行     | 第一列     | 第二列     |
 
 

