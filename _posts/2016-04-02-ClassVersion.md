---
layout: post
title: class文件版本问题
date: 2016-04-02
tag: java 
--- 

## class文件版本问题

##### 高版本jdk编译的class文件在低版本的jdk下有时会不支持，报异常  
java.lang.UnsupportedClassVersionError  
  
 major version 和jdk版本对关系如下  
   
    

Major version | 	Java
---|---
46 | Java 1.2
47 | Java 1.3
48 | Java 1.4
49 | Java 5
50 | Java 6
51 | Java 7

##### 查看class文件版本方法

cd 到class文件所在路径  
执行 javap -verbose XXX.class  
会看到如下结果  

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2439972-52678ecc1f13e99b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<br>

转载请注明：[FANER ARTIST的博客](https://peter2116.github.io) » [点击阅读原文](https://peter2116.github.io/2016/04/ClassVersion/)    







