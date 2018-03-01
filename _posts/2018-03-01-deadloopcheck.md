---
layout: post
title: 排查java应用中的死循环
date: 2018-03-01
tag: java 
--- 


>web应用中出现deadloop问题会导致机器cpu飙升，下面是一个常规的排查思路

### 查找进程pid  


利用`top` 或`ps -ef ` 或`jps` 命令找到吃cpu的pid,我们利用`top`   
![image](https://raw.githubusercontent.com/peter2116/ImgRep/master/gitImgRep/1.png)

可以看到pid为3688的进程导致cpu飙升

### 定位java线程  
用`top -Hp 3688`定位到导致吃cpu的线程pid
![image](https://raw.githubusercontent.com/peter2116/ImgRep/master/gitImgRep/deadloop_3.png)  
将`23694`转化为十六进制为`0x5c8e`

### jstack获取堆栈信息
用`jstack`命令打印出堆栈信息到文件  

    jstack 3688 > 3688.log

### 定位代码
在`3688.log`中查找pid为`0x5c8e`的线程便可定位到相关代码  
![image](https://raw.githubusercontent.com/peter2116/ImgRep/master/gitImgRep/deadloop_2.png)

<br>

转载请注明：[FANER ARTIST的博客](https://peter2116.github.io) » [点击阅读原文](https://peter2116.github.io/2016/04/ClassVersion/)    







