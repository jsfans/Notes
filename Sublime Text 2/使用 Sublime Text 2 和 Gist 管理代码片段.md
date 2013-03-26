# 使用 Sublime Text 2 和 Gist 管理代码片段
------

结合 [Sublime Text 2][Sublime] 的 [Gist 插件][sublime-package-gist] 和 [Github][Github] 提供的 [Gist 代码片段分享平台][Gist] ，打造出一个能够很方便的进行创建、搜索插入、更新以及版本控制的代码片段管理器。

大致流程如下：

+   [建立一个 Gist 账户][Gist signup] 。

+ 	通过 [Package Control][Package Control] 安装 Gist 插件 。

   	注意：Sublime Text 2 本身并不自带 Package Control，需要自行安装。安装方法如下：

 1. 打开 Sublime Text 2，按下 ``Control + ` ``调出 Console。

 2. 将以下代码粘贴进命令行中并回车：

            import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())

 3. 重启 Sublime Text 2，如果在 Preferences -> Package Settings中见到Package Control这一项，就说明安装成功了。

+   Preferences -> Package Settings -> Gist -> Settings - User，填入 Gist 账户名及密码：

		{
			// Your username on GitHub
			"username": "your_user_name",

			// Your password on GitHub
			"password": "**********"

		}

    注意：此文件以明文形式保存 Gist 的账号和密码，需要妥善保管，万不可泄露他人。

+   创建新的代码片段：用 Sublime Text 2 建立空白文档，输入/粘贴需要的代码片段（无需保存），通过命令框（`⌘+⇧+P`，Windows系统：`Ctrl+Shift+P`）调用 `Gist:Creat Public Gist` 建立 Gist。或是用默认快捷键 （`⌘KI`按住⌘后按K及I，Windows系统：`Ctrl+KI`）。

    注意：由于 Gist 不提供分类，所以在输入 Description 时，最好使用“语言:名称”的形式以便于查找，如：“HTML: Starting Template”。

+   调用代码片段：通过命令框调用 Gist:Open Gist，或是快捷键 (`⌃⌘G`，Windows系统：`Ctrl+KO`)。

    这时可以通过搜索框进行过滤，借助 Sublime Text 2 的实时匹配，可以很容易的找到你需要的片段，按下回车就会在新标签中打开，然后就可以复制粘贴到需要的地方了。

+   更新代码片段：通过 Gist:Open Gist 打开的片段，可以在修改后通过 Gist: Update File 进行更新。

+   Gist 是一个代码分享平台，当你看到别人分享的优秀代码，可以直接 fork 过来为己所用。

笔记来源：<http://lucifr.com/2012/03/07/sublime-text-2-plus-gist-equal-snippet-manager/>

[Sublime]: http://www.sublimetext.com/
[Github]: https://github.com/
[Gist]: https://gist.github.com/
[Gist signup]: https://github.com/signup?return_to=gist
[sublime-package-gist]: https://github.com/condemil/Gist
[Package Control]: http://wbond.net/sublime_packages/package_control


