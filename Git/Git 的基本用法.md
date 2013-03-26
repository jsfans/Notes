# Git 的基本用法
------

总结一下 Git 的常用命令：

## 在工作目录中初始化新仓库

`$ git init`

初始化后，在当前目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。不过目前，仅仅是按照既有的结构框架初始化好了里边所有的文件和目录，但我们还没有开始跟踪管理项目中的任何一个文件。

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：

    $ git add *.c
    $ git add README
    $ git commit -m 'initial project version'

## 从现有仓库克隆

`$ git clone git://github.com/your_user_name/your_repo.git`

这会在当前目录下创建一个名为“grit”的目录

定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：
 
`$ git clone git://github.com/your_user_name/your_repo.git new_name`

下图表示文件状态的变化周期

<img src="https://app.yinxiang.com/shard/s2/res/2401ffc4-736e-435d-b66d-91e7712dd368.png?resizeSmall&width=1340" alt="">

## 检查当前文件状态

`$ git status`

## 跟踪新文件

`$ git add untracked_file`

这会把目标文件快照（或目录）放入暂存区域，用点号表示一次过跟踪所有文件：

`$ git add .`

## 忽略某些文件

要养成一开始就设置好 .gitignore 文件的习惯，以免将来误提交这类无用的文件：

文件 .gitignore 的格式规范如下：

* 所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
* 可以使用标准的 glob 模式匹配。
* 匹配模式最后跟反斜杠（/）说明要忽略的是目录。 
* 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
        
> 所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。星号（*）匹配零个或多个任意字符；[abc] 匹配任何一个列在方括号中的字符（这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）；问号（?）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如[0-9] 表示匹配所有 0 到 9 的数字）。

我们再看一个 .gitignore 文件的例子：
 
    # 此为注释 – 将被 Git 忽略
    *.a       # 忽略所有 .a 结尾的文件
    !lib.a    # 但 lib.a 除外
    /TODO     # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
    build/    # 忽略 build/ 目录下的所有文件
    doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt

## 查看已暂存和未暂存的更新

要查看尚未暂存的文件更新了哪些部分，不加参数直接输入 git diff：

`$ git diff`

若要看已经暂存起来的文件和上次提交时的快照之间的差异，可以用 git diff --cached 命令:

`$ git diff --cached`

### 提交更新

现在的暂存区域已经准备妥当可以提交了。在此之前，请一定要确认还有什么修改过的或新建的文件还没有 git add 过，否则提交的时候不会记录这些还没暂存起来的变化。所以，每次准备提交前，先用git status 看下，是不是都已暂存起来了，然后再运行提交命令 git commit：

`$ git commit`

默认会用vim打开提交的消息，另外开头还有一空行，供你输入提交说明，输入后保存退出，Git 会丢掉注释行，将说明内容和本次更新提交到仓库。

另外也可以用 -m 参数后跟提交说明的方式，在一行命令中提交更新：

`$ git commit -m "Story 182: Fix benchmarks for speed"`

### 跳过使用暂存区域

只要在提交的时候，给 git commit 加上-a 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤：

`$ git commit -a -m 'added new benchmarks'`

### 移除文件

要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），然后提交。可以用 git rm 命令完成此项工作，并连带从工作目录中删除指定的文件：

`$ git rm file_to_delete`


