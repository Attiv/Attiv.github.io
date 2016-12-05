---
layout: post
title: "Lumen项目 migrate Mysql "
date: 2016-11-28
comments: true
tags: 
        - Lumen
---
#lumen项目 migrate Mysql



1. 登录MySql 创建一个名字和lumen项目目录下.env文件里DB_DATABASE 名字一样的数据库.
2. 执行```php artisan migrate```
3. 进行填充,执行```php artisan db:seed```
4. 刷新数据库结构并执行数据填充 ```php artisan migrate:refresh --seed```
5. 需要添加字段的话在迁移里添加:

```
<?php
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;
class CreateFlightsTable extends Migration
{
    /**
     * 运行数据库迁移。
     *
     * @return void
     */
    public function up()
    {
        Schema::create('flights', function (Blueprint $table) {
            $table->increments('id');
            $table->string('name');
            $table->string('airline');
            $table->timestamps();
        });
    }

    /**
     * 回滚数据库迁移。
     *
     * @return void
     */
    public function down()
    {
        Schema::drop('flights');
    }
}

```
然后运行```php artisan migrate:refresh --seed```
