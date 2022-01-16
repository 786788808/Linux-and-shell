工作中常用到shell script实现调用，菜鸡mark here, 对自己学到的一些东西mark下来，以后好复习。   
### 1.什么是shell
刚开始接触shell的时候，只知道脚本以.sh结束，其脚本还带有linux命令……一脸问号  
慢慢……知道了一点东西  
shell，直译外壳，它是操作系统的外壳。我们可以通过shell命令来操作和控制操作系统。可理解成，Shell是一个命令解释器，它通过接受用户输入的Shell命令来启动、暂停、停止程序的运行或对计算机进行控制。  
说人话一点，可以把shell比喻成一个翻译官，我写了人类能看懂的脚本（ABCDEFG……），想要计算机去帮我干活，但是计算机它只懂机器语言（0101010101），在这种鸡同鸭讲的情况下，于是请来了shell来当翻译官，将人类的指令翻译成机器能识别的语言，然后让机器去干活。  
不过，我们常说的shell是shell script,重点在会读会写会用。  
### 2.shel的类比
Linux的Shell种类众多，常见的有：  
- Bourne Shell（/usr/bin/sh或/bin/sh）
- **Bourne Again Shell（/bin/bash）**
- C Shell（/usr/bin/csh）
- K Shell（/usr/bin/ksh）
- Shell for Root（/sbin/sh）
它们由不同的人或组织、实验室研发出来，我们常用的就是 Bourne Again Shell，缩写: bash .它是linux标准的默认shell ，它基于Bourne shell，吸收了C shell和Korn shell的一些特性。bash完全兼容sh，也就是说，用sh写的脚本可以不加修改的在bash中执行。  
可通过以下命令查询自己的linux支持什么shell：cat ./etc/shells  
输入vi /etc/shells，可看到linux支持什么shell    
![image](https://user-images.githubusercontent.com/32427537/149654418-efd18470-1a82-4481-909f-de9330839140.png)  
### 2.
