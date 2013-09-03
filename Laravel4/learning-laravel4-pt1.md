## Laravel 4 笔记整理1 - 环境的搭建

### 安装 composer

Laravel 4 使用 [composer](http://getcomposer.org/) 作为包管理器。要创建 Laravel 4 项目，必须先安装 composer。

[composer 的 github 仓库](https://github.com/composer/composer)提供了几种安装方法，其中使用 homebrew 来安装是最简单直接的方法：

	brew tap josegonzalez/homebrew-php
	brew install josegonzalez/php/composer

安装完毕后运行 `composer` 命令，如果输出 composer 的帮助信息则说明安装成功。
	

### 创建项目

使用 composer 的 `create-project` 命令创建项目：

	composer create-project laravel/laravel your-project-name --prefer-dist

创建好的 Lavavel 4 基本文件结构及功能如下：

	your-project-name/       # 项目根目录
	`-- app/                 # 主程序
	|   `-- command/         # 
	|   `-- config/          # 主配置
	|   `-- controllers/     # 控制器类
	|   `-- database/
	|       `-- migrations/  # 数据库迁移
	|       `-- seeds/       # 存放种子文件
	|   `-- lang/            # 多语言
	|   `-- models/          # 存放模型类
	|   `-- start/           # 
	|   `-- storage/         #
	|   `-- tests/           # 存放测试
	|   `-- views/           # 视图
	|   `-- filters.php      # 所有过滤器都放在这个文件中
	|   `-- routes.php       # 路由设置
	`-- bootstrap/           # 
	|   `-- autoload.php     # 自动加载
	|   `-- paths.php        # 路径约定
	|   `-- start.php        # 启动文件
	`-- public/              # 前端文件、网站入口
	`-- vendor/              # Laravel 4 框架
	`-- composer.json        # composer 配置文件
	`-- phpunit.xml          # 单元测试配置文件
	`-- server.php           # Apache 服务模拟器

其中 `app/config` 存放跟整个应用相关的配置文件，非常重要，其文件结构及功能如下：

	app/
	 `-- config/
	     `-- packages/       #
	     `-- testing/        #
	     `-- app.php         # 应用程序配置
	     `-- auth.php        # 用户身份验证
	     `-- cache.php       #
	     `-- compile.php     #
	     `-- database.php    # 数据库连接配置
	     `-- mail.php        #
	     `-- queue.php       #
	     `-- session.php     #
	     `-- view.php        #
	     `-- workbench.php   #	      

### 安装第三方包

为了能更快速的进行开发，需要以下的第三方包：

+ [Laravel-4-Generators](https://github.com/JeffreyWay/Laravel-4-Generators)：骨架代码生成器(JeffreyWay/Laravel-4-Generators)

+ [Sentry](http://docs.cartalyst.com/sentry-2/installation/laravel-4)：用户身份验证(cartalyst/sentry)

+ [Imagine](http://imagine.readthedocs.org/cn/latest/)：图像处理(imagine/Imagine)

安装步骤如下：

1. 打开 composer.json 给 `require` 项添加相应的配置信息：

		{
			"require": {
				"laravel/framework": "4.0.*",
				"way/generators": "dev-master",
				"cartalyst/sentry": "2.0.*",
				"imagine/Imagine": "v0.5.0"
			},
			"autoload": {
			…
		}

2. 更新 composer：

		composer update

3. 在 `app/config/app.php` 中添加服务提供者和类别名的信息：

		'providers' => array(
			…
			'Cartalyst\Sentry\SentryServiceProvider',
			'Way\Generators\GeneratorsServiceProvider',
		);
		
		'aliases' => array(
			…
			'Sentry' => 'Cartalyst\Sentry\Facades\Laravel\Sentry',
		);


### 配置开发环境

使用 `hostname` 命令取得机器名称，将 `bootstrap/start.php` 中的 `'your-machine-name'` 修改成机器名称，比如：

	$env = $app->detectEnvironment(array(
		'local' => array('seishitekiMacBook-Pro.local'),
	);

在 `app/config` 目录中创建 `local` 目录：

	mkdir app/config/local
	
这样，如果是本地环境，就会自动读取 `local` 目录中的配置文件，以覆盖默认设置。


### 一些额外的配置

接着生成一个用于加密的32位密钥：

	php artisan key:generate

最后 `app/storage` 目录需要拥有写权限:
	
	chmod -R 0777 app/storage

    
