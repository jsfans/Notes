# Vundle 的安装
------

## 安装Git

Vundle在Linux非常容易安装，在Windows下首先需要安装Git。

下载 [msysgit][msysgit] 并安装。同时建议安装一个 [TortoiseGit][TortoiseGit] 作为图形界面。
 
Git安装后将Git的路径加入系统环境变量，win7下Git的路径为
 
C:\Program Files (x86)\Git\cmd
 
然后运行cmd，输入

`git --version`

如果能显示Git版本信息，说明安装成功

`git version 1.7.10.msysgit.1`

在Win32下还需要建立一个Curl脚本用于Vundle的远程链接。在Git的路径下新建一个空文本文件，改名为curl.cmd，编辑内容为：

	@rem Do not use "echo off" to not affect any child calls. 
	@setlocal
	 
	@rem Get the abolute path to the parent directory, which is assumed to be the
	@rem Git installation root.
	@for /F "delims=" %%I in ("%~dp0..") do @set git_install_root=%%~fI
	@set PATH=%git_install_root%\bin;%git_install_root%\mingw\bin;%PATH%
	 
	@if not exist "%HOME%" @set HOME=%HOMEDRIVE%%HOMEPATH%
	@if not exist "%HOME%" @set HOME=%USERPROFILE%
	 
	@curl.exe %*

保存后在cmd中输入：

`curl --version`

如果可以看到版本信息说明运行成功。

## 安装Vundle

Git安装完毕后，打开Cmd窗口，使用以下命令Clone Vundle到”D:\Vim\vimfiles\bundle”下：

	git clone http://github.com/gmarik/vundle.git ~/.vim/bundle/vundle

此时目录结构应该如下：

	D:\vim
    +---vim73
    +---vimfiles
        +---bundle
        |   +---vundle
        +---colors

## 配置Vundle

按照Vundle官方给出的配置，所有通过Vundle安装的插件会被安装到Windows的用户目录下，这里我做了修改，直接安装到Vim目录下更加方便管理。

编辑_vimrc加入：

	" 必须先关闭文件类型检查
	filetype off
	 
	"此处规定Vundle的路径
	set rtp+=$VIM/vimfiles/bundle/vundle/
	 
	"此处规定插件的安装路径
	call vundle#rc('$VIM/vimfiles/bundle/')
	
	" Vundle自更新 
	Bundle 'gmarik/vundle'

	" 需要安装的插件列表放在这里
	 
	" 重新打开文件类型检查
	filetype plugin indent on
 
## 通过Vundle 安装插件

Vundle安装插件有三种形式，一种是一个从官方移植的Vim Script,只需要在配置中写脚本的名字，比如：
 
`Bundle 'neocomplcache'`
 
第二种是指定一个github上的项目名，以作者/项目的形式：
 
`Bundle 'gmarik/vundle'`
 
最后还可以指定一个完整的git repos地址：
 
`Bundle 'git://git.wincent.com/command-t.git'`
 
将要安装的插件在配置文件中写好，最后执行：
 
`:BundleInstall`
 
就可以一键安装了。安装有问题可以按l键查看log。我在第一次安装时出现了“can't resolve proxy 'null' for https”的报警，调查发现是因为git启用了代理的原因，可以运行cmd：
 
`git config --global --unset http.proxy`
 
## Vundle 常用指令
 
+ `:BundleList` 列出已经安装的插件
+ `:BundleInstall` 安装所有配置文件中的插件
+ `:BundleInstall!` 更新所有插件
+ `:BundleSearch` 搜索插件
+ `:BundleClean!` 根据配置文件删除插件

附上我自己的插件配置：

	"------------------
	" Code completions
	"------------------
	Bundle 'Shougo/neocomplcache'
	Bundle 'garbas/vim-snipmate'
	Bundle 'honza/snipmate-snippets'
	Bundle 'ervandew/supertab'
	" Snipmate dependencies
	Bundle 'MarcWeber/vim-addon-mw-utils'
	Bundle 'tomtom/tlib_vim'

	"------------------
	" Fast navigation
	"------------------
	" Extended '%' matching
	Bundle 'tsaleh/vim-matchit'
	" Fast jumping from lines
	Bundle 'Lokaltog/vim-easymotion'

	"------------------
	" Fast editing
	"------------------
	Bundle 'jiangmiao/auto-pairs'
	Bundle 'scrooloose/nerdcommenter'
	" Undo list
	Bundle 'sjl/gundo.vim'
	Bundle 'nathanaelkane/vim-indent-guides'

	"------------------
	" IDE
	"------------------
	Bundle 'scrooloose/nerdtree'
	Bundle 'majutsushi/tagbar'
	" Grep files
	Bundle 'mileszs/ack.vim'
	Bundle 'kien/ctrlp.vim'
	" Git wrapper
	Bundle 'tpope/vim-fugitive'
	" Pretty status line
	Bundle 'Lokaltog/vim-powerline'
	" Syntax checking
	Bundle 'scrooloose/syntastic'
	Bundle 'walm/jshint.vim'

	"------------------
	" Syntax Highlight
	"------------------
	" Web front end
	Bundle 'othree/html5.vim'
	Bundle 'nono/jquery.vim'
	Bundle 'pangloss/vim-javascript'
	" Web back end
	Bundle '2072/PHP-Indenting-for-VIm'
	" Markdown
	Bundle 'tpope/vim-markdown'

本文主要参考： <http://avnpc.com/pages/vim-of-allovince>

[msysgit]: http://code.google.com/p/msysgit/downloads/list
[TortoiseGit]: http://code.google.com/p/tortoisegit/

