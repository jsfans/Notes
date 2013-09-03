Date: 2013-07-26
Title: 如何在Mac OS中安装wget
Tags: wget,mac
Slug: install-wget-on-mac

wget 是一个命令行的下载工具。

下载 xcode 及其命令行工具进行安装；

然后下载Wget 安装：

	curl -O http://ftp.gnu.org/gnu/wget/wget-1.13.4.tar.gz
	tar -xzvf wget-1.13.4.tar.gz
	cd wget-1.13.4
	./configure --with-ssl=openssl
	make
	sudo make install
