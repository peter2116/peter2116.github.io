---
layout: post
title: macOs mysql安装与卸载
date: 2016-04-02
tag: mysql
--- 


### 安装MySql服务  

### 切换到root 用户  
    sudo -i

### 解压安装包并移动到指定了路径/usr/local  
    tar -zxvf mysql-5.7.13-osx10.11-x86_64.tar  
    sudo mv mysql-5.7.13-osx10.11-x86_64 /usr/local/mysql  

### 更改目录的用户和用户组  
    cd /usr/local   
    sudo chown -R root:wheel mysql

### 执行bin目录下的mysqld脚本完成初始化(创建默认配置文件、授权表等)  
    cd /usr/local/mysql  
    sudo bin/mysqld --initialize --user=mysql   
     
执行完成之后会root用户随机分配一个密码,这个密码需要记录好，以备用来登录后修改root密码。  
一般会显示：2017-04-20T06:10:09.073666Z 1 [Note] A temporary password is generated for root@localhost: BxnS<>qpD8E4, BxnS<>qpD8E4这个就是root用户分配的随机密码  
如果之后找不到，尝试到mysql/data 路径下的XXX.err文件内找  

### 安装完成后常用的一些脚本 
    cd /usr/local/mysql   
    启动        
    sudo support-files/mysql.server start     
    重启      
    sudo support-files/mysql.server restart      
    停止      
    sudo support-files/mysql.server stop      
    检查 MySQL 运行状态         
    sudo support-files/mysql.server status      

### 为了方便可以将mysql的bin，和support-files添加到PATH 

    export  PATH=$PATH:/usr/local/mysql/support-files
    export  PATH=$PATH:/usr/local/mysql/bin




### mysql卸载  

    sudo rm /usr/local/mysql
    sudo rm -rf /usr/local/mysql*
    sudo rm -rf /Library/StartupItems/MySQLCOM
    sudo rm -rf /Library/PreferencePanes/My*
    vim /etc/hostconfig  (and removed the line MYSQLCOM=-YES-)
    rm -rf ~/Library/PreferencePanes/My*
    sudo rm -rf /Library/Receipts/mysql*
    sudo rm -rf /Library/Receipts/MySQL*
    sudo rm -rf /var/db/receipts/com.mysql.*



<br>
转载请注明：[FANER ARTIST的博客](https://peter2116.github.io) » [点击阅读原文](https://peter2116.github.io/2016/07/Facade/)  


