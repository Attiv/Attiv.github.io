---
layout: post
title: "Apache 3个常用命令,Mysql无法开启的问题 "
date: 2016-11-24 
comments: true
tags: 
        - Apache Mysql
---

##Apache 3个常用命令

 - 开启Apache: ``` sudo apachectl start ```
 
 - 关闭Apache: ``` sudo apachectl stop ```
 
 - 重启Apache: ``` sudo apachectl restart ```  
 

##lumen项目 migrate Mysql

1. 登录MySql 创建一个名字和lumen项目目录下.env文件里DB_DATABASE 名字一样的数据库.
2. 执行```php artisan migrate```
3. 进行填充,执行```php artisan db:seed```

##Mysql无法开启的问题

Mysql在无论怎么安装卸载修改变量都无法开启成功的情况下,可以尝试删除Mysql,然后用 [老版本](链 https://pan.baidu.com/s/1qYrmAZU) 密码: ```teu1``` 安装,通过系统偏好设置的Mysql点击开启,使用``` /usr/local/mysql/bin/mysql```进入数据库,
mysql默认密码为空，修改密码``` mysqladmin -uroot password "密码"```   例如 修改密码为root   ```mysqladmin -uroot password root```


