Date: 2013-07-26
Title: Mac神器系列之autojump
Tags: autojump,zsh,mac
Slug: play-with-autojump

### 简介

在 Mac 的任何一个 shell 里面，一般的切换目录所使用的命令是 cd (change directory)。

使用过 cd 命令的程序猿都知道，要 cd 到一个很深的目录是一件很悲催的事情，因为大多数人只记得最底层的目录名称，而这个名称往往就是所需要 cd 到的目录。

autojump 解决了这种困扰！

### 安装 autojump

用 homebrew 安装：

	brew install autojump

安装完成后会提示将以下这句添加到 zsh 的配置文件 `~/.zshrc`：

	[[ -s `brew --prefix`/etc/autojump.sh ]] && . `brew --prefix`/etc/autojump.sh

source 一下使之生效：

	source ~/.zshrc

至此，autojump 安装完毕。以后你去过的目录都会被 autojump 记录，当然，第一次切换到的目录还是需要使用 cd 指令的。

### 使用 autojump

autojump 的使用单字符 `j` 指令：

	j <目标目录>
	
例如输入：

	j word

切换到名称包含 word 并且最经常切换的目录。

如果有两个同名的目录，再运行 `j word` 会跳到第二个符合的目录，若再运行 `j word` 则又跳回第一个目录。

如果有三个或以上同名的目录，则需要使用 Tab 键查找，例如输入：

	j word<Tab>

则会帮你列出符合条件的目录清单：

	~$ j word__
	word__1__/usr/share/wordpress  word__2__/etc/wordpress

此列表的意思是，第1个符合的是/usr/share/wordpress，第2个符合的是/etc/wordpress，如果想跳转到/etc/wordpress，输入2再回车就可以。

最后，执行 `j -s` 可以看到 autojump 的统计表，权重越高的表示越去得多次。