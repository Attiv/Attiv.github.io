---
layout: post
title: "初学PHP Laravel "
date: 2016-12-01
comments: true
tags: 
        - Laravel
---
# 初学PHP Laravel
---

## 不用Apache改用Valet
**Valet 要求 mac 操作系统和 Homebrew。安装之前，你需要确保没有其他程序如 Apache 或者 Nginx 占用你本地机器的 80 端口。**

 安装步骤如下：

 - 安装或者更新 Homebrew 到最新版本,使用命令: `brew update`


 - 使用 `brew install homebrew/php/php70` 命令安装 PHP 7.0 。
 - 通过 Composer 安装 Valet 命令为 `composer global require laravel/valet`。 请确保 ~/.composer/vendor/bin 目录在系统环境变量 「PATH」 中。如果不在,可以用命令:`export PATH="$PATH:$HOME/.composer/vendor/bin"`导入,然后输入:`source ~/.bashrc`
 - 运行 `valet install` 命令。 这将会配置并安装 Valet 和 DnsMasq，并注册 Valet 随你的系统启动。

一旦完成 Valet 安装，试着使用命令如` ping foobar.dev` 在终端 ping 一些任意的*.dev 域名。如果 Valet 安装正确你会看到来自 127.0.0.1 的响应。

**使用其他顶级域名**

默认的，Valet 使用 .dev 顶级域名。如果你喜欢其他域名，可以使用 `valet domain tld-name`命令,不建议使用`www`开头和`com`结尾。

例如，如果你想使用 .app 来替换 .dev，运行` valet domain app `然后 Valet 将会自动的使用 *.app 来为你的项目提供服务。

你可以使用 `composer global update` 命令升级你的 Valet 程序，升级之后，最好使用 `valet install` 命令更新 Valet 的配置文件。

## 服务站点

一旦完成 Valet 安装，你就可以启动服务站点，Valet 提供两个命令帮助你启动你的 Laravel 站点： `park` 和 `link`。

**`park` 命令**

- 在你的 Mac 中创建一个新目录，例如` mkdir ~/Sites` ，然后，使用` cd ~/Sites `并运行 `valet park`。这个命令将会将当前所在目录作为 Web 根目录， Valet 将会在这个目录中搜索站点。
- 接下来，在这个目录中创建一个新的 Laravel 站点：`laravel new blog`。
在浏览器中访问 http://blog.dev 。

这就是我们要做的全部工作 现在，所有在 Site 目录中的 Laravel 项目都可以通过 http://folder-name.dev 这种方式访问，是不是很方便。

**`link` 命令**

link 命令可以用于你的本地 Laravel 站点。这个命令在你想要在目录中提供单个站点是很有用。

- 要使用这个命令，在你的终端中切换到你的某个项目并运行 `valet link app-name`。 Valet 将会在 ~/.valet/Sites 中创建一个符号链接并指向当前工作目录。
- 运行完 link 命令, 你可以在浏览器中通过 http://app-name.dev 来访问站点。
要查看所有的链接目录，运行 `valet links `命令。你也可以通过 `valet unlink app-name `来删除符号链接。

## 构建完整站点等
 参考[官方文档](https://laravel-china.org/docs/5.3/valet#serving-sites)

**要求输入的参数条件**

 ```
  try {
            $this->validate($request, [
                'currency_date' => 'required|min:6|max:10',
                'currency' => 'required',
            ]);
        } catch (HttpResponseException $e) {
            return response()->json([
                'success'   => false,
                'message'   => 'date-formatter is wrong.',
                'error'     => IlluminateResponse::HTTP_BAD_REQUEST
            ], IlluminateResponse::HTTP_BAD_REQUEST);
        }
```


**查询字符串中以...开头**


```
    $result = Currency::where('currency_date','like',$date.'%')->get();
```
 

