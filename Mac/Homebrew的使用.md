## Homebrew 的安装

Homebrew 依赖于 Xcode 和 ruby。Mac 自带 ruby，Xcode 只能在 Mac 的 App store 里面下载，有点大。

安装完 Xcode 后，运行下面的命令安装 Homebrew：

	ruby -e "$(curl -fsSLk https://gist.github.com/raw/323731/install_homebrew.rb)"

## Homebrew 的使用

下边我们以安装和管理git为例，演示如何使用Homebrew。

### 1.安装软件

	brew install git
	
### 2.卸载软件

	brew uninstall git
	
### 3.搜索软件

	brew search git
	
### 4.	更新软件

	brew upgrade git
	
### 5.删除软件

	brew cleanup git
	
### 6.检查软件更新

	brew outdated
	
### 7.更新所有软件

把所有的Formula目录更新，并且会对本机已经安装并有更新的软件用*标明。

	brew upgrade
	
### 8.显示已经安装的软件

	brew list

### Homebrew的安装路径及文件夹

Homebrew将本地的/usr/local初始化为git的工作树，并将目录所有者变更为当前所操作的用户，以后的操作将不需要sudo。

	-bin          用于存放所安装程序的启动链接（相当于快捷方式）
	-Cellar       所以brew安装的程序，都将以[程序名/版本号]存放于本目录下
	-etc          brew安装程序的配置文件默认存放路径
	-Library      Homebrew 系统自身文件夹
	
## Homebrew 的卸载

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
	
## Homwbrew 使用实践

### Nodejs 的安装

只需要一句命令完成 Node 的安装：`brew install node`