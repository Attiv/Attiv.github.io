---
layout: post
title: "Mac 下配置 apache PHP mysql "
date: 2016-12-01 13:54
comments: true
tags: 
        - PHP
---

# Mac 下配置 apache PHP mysql 
---
## 步骤
 - 安装 homebrew
 - 安装 php (mac 默认有PHP 版本 )查看本机php版本：php -v
 - 配置apache（mac默认有apache）   vhost
 - 安装mysql 
 - 配置 hosts
 - 安装 npm 

### 安装homebrew
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


### 安装：apache php版本（选装 mac自带apache php）
```
brew tap homebrew/apache
brew tap homebrew/php
brew install httpd24
brew install php53
```

### 安装Mysql
```
brew install mysql
```

(可以用`brew info mysql` 查询信息)


### 配置mac 自带apache
重启 apache服务器 `sudo apachectl restart` 

查看80端口 `netstat -anl | grep "80"`

地址： /etc/apache2/httpd.conf (可先复制备份一份  sudo cp /etc/apache2/httpd.conf /etc/apache2/httpd.conf.backup )

在http.conf中 有Listen 80 即为监听80端口

"#LoadModule php5_module libexec/apache2/libphp5.so 将#删除 配置mac自带的php版本  "

如果本地mac 自带php版本过低 需升级。
[php版本过低想升级](http://weiww.jianshu.com/p/0456dd3cc78b)

 在httpd.conf 加入引用本地php的配置 LoadModule php5_module  /usr/local/php5-5.6.27-20161101-100213/libphp5.so（自己的路径）
 
 配置apache ->/etc/apache/extra/httpd-vhosts.conf (最好备份)
 
 ```
 <VirtualHost *:80>
    ServerAdmin xxx.xxx.xxx
    DocumentRoot "项目路径/public(如果是前段项目就没有public)"
    ServerName xxx.xxx.xxx
    #DirectoryIndex index.php
    ErrorLog "/private/var/log/apache2/sites-error_log"
    CustomLog "/private/var/log/apache2/sites-access_log" common

 <Directory  "项目路径/public(同上)>
 Options FollowSymLinks
 AllowOverride All
 Order allow,deny
 allow from all
 Require all granted  
 </Directory>
</VirtualHost>
 ```
 
 端口号为：80
  DocumentRoot "/Users/****/projects/webtailor-backend/public"  配置后端入口 在项目的public目录下 后端代码 不要放在桌面上 最好在/users目录下 新建一个项目文件夹

配置apache ->/etc/hosts (最好备份),增加一个域名指向127.0.0.1
 [参考](https://my.oschina.net/joanfen/blog/171109)
 


### Lumen
后台:
Comopser 安装 项目根目录

```
composer install
```

```
composer require basicit/lumen-vendor-publish
```

```
composer dump-autoload
```
前端：
`npm install -g npm`

`npm install -g gulp`

每次改完代码执行

`gulp build`

如果不想每次都执行可以用
` gulp watch`


### 配置数据库  
启动 mysql 

`mysql.server start`

查看mysql 是否运行

`brew services list`

`netstat -anl | grep "3306"`

mysql默认密码为空，修改密码 

`mysqladmin -uroot password "密码"`

->修改密码为root:   `mysqladmin -uroot password root`

[mysql2000错误](http://stackoverflow.com/questions/15016376/cant-connect-to-local-mysql-server-through-socket-homebrew)

创建可以用可视化软件

 

