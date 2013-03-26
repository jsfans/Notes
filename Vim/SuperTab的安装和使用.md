# Vim插件-SuperTab的安装和使用
------

SuperTab使Tab快捷键具有更快捷的上下文提示功能。

## 安装

使用 Vundle 安装：`Bundle 'ervandew/supertab'`。

## 配置

添加如下配置：`let g:SuperTabDefaultCompletionType="context"`

## 使用

SuperTab使用很简单，只要在输入变量名或路径名等符号中途按Tab键，就能得到以前输入过的符号列表，并通过Tab键循环选择。