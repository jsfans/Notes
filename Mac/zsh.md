Date: 2013-07-26
Title: Mac神器系列之zsh
Tags: zsh,shell,mac
Slug: play-with-zsh

zsh 绝对是 Mac 上最好用的 shell，没有之一。

### 安装 zsh

	brew install zsh

### 设置 zsh 为默认 shell

	vi /etc/shells

在末尾增加：

	/usr/local/bin/zsh

设置为默认 shell：

	chsh -s /usr/local/bin/zsh

重启 Terminal。

附上 linux 命令 chsh 的说明：

> chsh(change shell)
> 
> **功能说明：**更换登入系统时使用的shell。
> 
> **语法：**chsh [-luv][-s <shell 名称>][用户名称]
> 
> **补充说明：**每位用户在登入系统时，都会拥有预设的shell环境，这个指令可更改其预设值。若不指定任何参数与用户名称，则chsh会以应答的方式进行设置。
> 
> **参数：**  
> -s\<shell 名称>或--shell\<shell 名称> 　更改系统预设的shell环境。   
> -l或--list-shells 　列出目前系统可用的shell清单。  
> -u或--help 　在线帮助。  
> -v或-version 　显示版本信息。

### 配置 zsh

若是 DIY zsh 的配置估计比配置 VIM 还要难。还好，已经有现成的配置让我们安装，那就是 oh-my-zsh。

安装 oh-my-zsh 有两种自动安装的方式：

1. 通过 curl：

		curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh

2. 通过 wget：

		wget --no-check-certificate https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh

然后修改 .zshrc：

	vi .zhsrc

将原来 .bash_profile 与 .profile 中的自定义内容拷贝过来。

比如支持rvm，应在.zshrc增加：

	[[ -s $HOME/.rvm/scripts/rvm ]] && source $HOME/.rvm/scripts/rvm

并自定义 .zhsrc 文件, 比如更换 robbyrussell 这个 theme：

	export ZSH_THEME="robbyrussell" 

完整的 theme 方案列表在[这里](https://github.com/robbyrussell/oh-my-zsh/wiki/themes)

 
 