## 软件包管理系统 Homebrew 的安装与使用

### Homebrew 的安装

Homebrew 依赖于 Xcode 和 ruby。Mac 自带 ruby，Xcode 只能在 Mac 的 App store 里面下载，有点大。

安装完 Xcode 后，运行下面的命令安装 Homebrew：

	ruby -e "$(curl -fsSLk https://gist.github.com/raw/323731/install_homebrew.rb)"

### Homebrew 的使用

下边我们以安装和管理git为例，演示如何使用Homebrew。

#### 1.安装软件

	brew install git
	
#### 2.卸载软件

	brew uninstall git
	
#### 3.搜索软件

	brew search git
	
#### 4.	更新软件

	brew upgrade git
	
#### 5.删除软件

	brew cleanup git
	
#### 6.检查软件更新

	brew outdated
	
#### 7.更新所有软件

把所有的Formula目录更新，并且会对本机已经安装并有更新的软件用*标明。

	brew upgrade
	
#### 8.显示已经安装的软件

	brew list

#### 9.Homebrew的安装路径及文件夹

Homebrew将本地的/usr/local初始化为git的工作树，并将目录所有者变更为当前所操作的用户，以后的操作将不需要sudo。

	-bin          用于存放所安装程序的启动链接（相当于快捷方式）
	-Cellar       所以brew安装的程序，都将以[程序名/版本号]存放于本目录下
	-etc          brew安装程序的配置文件默认存放路径
	-Library      Homebrew 系统自身文件夹
	
### Homebrew 的卸载

万一用得不爽了，卸载之：

	cd `brew –prefix`

    rm -rf Cellar

    brew prune 

    rm `git ls-files` 

    rm -rf Library .git .gitignore bin/brew

    rm  -rf README.md share/man/man1/brew

    rm -rf Library/Homebrew Library/Aliases 

    rm -rf Library/Formula Library/Contributions

    rm -rf ~/Library/Caches/Homebrew

## Sublime Text 2 的配置

### Package Control

1. Control + ` 调出 Sublime 的命令行；
2. 将以下代码粘贴进命令行中并回车：
	
		import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())
	
3. 重启 Sublime Text 2，如果在 Preferences -> Package Settings中见到Package Control这一项，就说明安装成功了。

### 代码片段

1. 使用 Package Control 安装 Emmet 插件；
2. 添加如下配置信息，禁用 Emmet 的 CSS Snippet 功能：

    	{
			"disable_tab_abbreviations_for_scopes": "source.css, source.scss"
    	}
   
### Javascript 语法检测

1. 命令行安装 node：

		brew install node

2. 使用 npm 安装 jshint：

		npm install -g jshint

3. 使用 Package Control 安装 JsHint 插件；

4. 使用 Package Control 安装 SublimeOnSaveBuild 插件，让其可以在 js 文件保存时自动检测。

### Markdown 的使用

1. **修改保存 Markdown 文件的后缀为 .md**
	新建 Markdown.sublime-settings 保存以下内容，并丢入 Packages/User/
	
		{
			"extensions": ["md"]
		}

2. **设置新建文件默认为 Markdown 格式**
   - 使用 Package Control 安装 Default File Type;
   - 新建 default_file_type.sublime-settings 保存以下内容，并丢入 Packages/User/

			{
				"default_new_file_syntax":"Packages/Markdown/Markdown.tmLanguage",
				"use_current_file_syntax":true
			}
	
3. **自定义 Markdown 高亮配色方案**
   - 默认 Packages/Color Scheme - Default/Monokai.thTheme 配色里是没有MD高亮的，所以网上搜来份并微调之，点击下载： Monokai-custom.tmTheme ；
   - 为避免之后主程序升级覆盖，把下载到的文件丢入 Packages/User/ ；
   - 打开 Packages/User/Preferences.sublime-settings 加入以下这条
	
			{
				"color_scheme": "Packages/User/Monokai-custom.tmTheme"
			}

4. **一键导出 HTML 代码**；
   - 使用 Package Control 安装 Markdown2Clipboard ；
   - 在 MD 文件中直接鼠标右键 Copy Markdown as HTML ;
	
5. **Markdown相关插件**
   - Markdown Preview - 预览 Markdown
   - SmartMardown - 智能的 Markdown 书写

### 其他插件

- JsFormat：Javascript 格式化
- Tag：HTML 格式化
- ClipBoard History：使用剪贴板记录
- Gist：使用 Github 提供的代码片段存储服务。（这个貌似很难连上…）
- SCSS：让 Sublime 支持 SCSS 语法
- Nettuts+ Fetch：方便常用库文件更新
- SideBarEnhancements：侧栏右键增强插件
- Soda：好看的皮肤插件

## 搭建 PHP 运行环境

Mac OS X 系统其实已经集成了 Apache+PHP环境，用户手动开启即可。

### 启用 Apache/Web 共享

打开终端，运行启动 Apache 的命令：

	sudo apachectl start

启动 Apache 后，在浏览器中访问：http://localhost，如果出现“It works!”就表示 Apache 正常运行。

Apache 的其他常用命令有：

- 关闭：

		sudo apachectl stop
	
- 重启：

		sudo apachectl restart

- 查看 Apache 版本：

		httpd -v

Mountain Lion 中集成的 Apache 版本如下：

> mbp:~ eyon$ httpd -v  
> Server version: Apache/2.2.22 (Unix)  
> Server built: Jun 20 2012 13:57:09

### 更新系统自带的 PHP

Mac 自带的 PHP 版本为5.3，三行代码升级到5.4，前提是已安装 Homebrew：

	brew tap homebrew/dupes
	brew tap josegonzalez/homebrew-php
	brew install php54

这样安装的php路径在/usr/local/bin/php，版本信息：

> /usr/local/bin/php -v  
> PHP 5.4.4 (cli) (built: Jul 27 2012 08:42:32)  
> Copyright (c) 1997-2012 The PHP Group  
> Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies

### 启用 PHP

在终端输入：

	sudo vim /etc/apache2/httpd.conf

将以下这句代码前面的#去掉：

	LoadModule php5_module libexec/apache2/libphp5.so

保存文件，重启 Apache：

	sudo apachectl restart

### 添加虚拟主机

在终端输入：

	sudo vim /etc/apache2/httpd.conf

在文档末加入如下代码，以实现单IP对应多个虚拟主机配置文件。

	NameVirtualHost *:80                                                                            
	Include /private/etc/apache2/other/*.conf
	Include /Users/你的用户名/vhost/*.conf

在用户目录下创建 vhost 目录，在该目录内为每一个虚拟主机独立创建一个配置文件，以下为配置文件的格式：

	<VirtualHost *:80>                                                                              
		ServerAdmin 随便填个邮箱
		DocumentRoot "/Users/seishizhang/Sites/项目目录"
		ServerName 虚拟主机域名
		#ErrorLog "/private/var/log/apache2/demo.gaofen.com-error_log"
		#CustomLog "/private/var/log/apache2/demo.gaofen.com-access_log" common
		<Directory "/Users/seishizhang/Sites/项目目录">
			Options Indexes FollowSymLinks MultiViews
			AllowOverride None
			Order deny,allow
			Allow from all
		</Directory>
	</VirtualHost>

添加完毕后，重启 Apache：

	sudo apachectl restart

终端输入：

	sudo vim /etc/hosts

为每个虚拟主机配置 IP 映射

终端输入：

	sudo vim /项目主目录/info.php

创建 info.php 文件并加入如下内容：

	<?php phpinfo(); ?>
	
如此就可以在http://虚拟主机域名/info.php中看到有关PHP的信息。

### MySQL 的安装与配置

MySQL 可以使用运行软件包的方式安装，而使用 Homebrew 安装会简单很多，一句命令安装：

	brew install mysql

安装完后还需要进行一些配置使 MySQL 生效：

	mkdir -p ~/Library/LaunchAgents
	cp /usr/local/Cellar/mysql/5.5.25a/homebrew.mxcl.mysql.plist ~/Library/LaunchAgents/
	launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist

	unset TMPDIR
	mysql_install_db --verbose --user=你的用户名 --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp

	/usr/local/Cellar/mysql/5.5.25a/bin/mysqladmin -u root password 'YOUR_NEW_PASSWORD'

	mysql.server start

## 其他

- CleanMyMac - 缓存文件清理、软件卸载
- Versions - 版本管理
- Phothshop
- Microsoft Office
- xScope - 屏幕拾色、尺寸量度
- Mou - Markdown 专用编辑软件
- Parallels Desktop - 虚拟机
- MacVim - 编辑器之神，不必多说
- TotalFinder - 可以让 Finder 拥有类似 Chrome 的标签式浏览功能
- Evernote - 做笔记
- Pocket - 剪报