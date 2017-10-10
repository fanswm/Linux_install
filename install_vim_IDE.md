> 文中用到的一些用<>括起来的符号比如<C-T>, <C-S-A>, 之类的, 你可以用下面的命令看看解释:
`:help keycodes`

## 安装中文帮助文件：
+ 下载vimcdoc-1.8.0.tar.gz
+ `tar zxvf ./vimcdoc-1.8.0.tar.gz`
+ `cd vimcdoc-1.8.0`
+ `./vimcdoc.sh -i`
> 参见README INSTALL

+ 查看是否装成功
+ ':help'

+ 设置中文帮助文档：`set helplang=cn`
+ 设置英文帮助文档：`set helplang=en`
+ `set encoding=utf-8`

## 常用的一些命令:
	+ %	跳转到配对的括号去
	+ [[	跳转到代码块的开头去(但要求代码块中'{'必须单独占一行)
	+ gD	跳转到局部变量的定义处
	+ ''	跳转到光标上次停靠的地方, 是两个', 而不是一个"
	+ mx	设置书签,x只能是a-z的26个字母
	+ `x	跳转到书签处("`"是1左边的键)
	+ >	增加缩进,"x>"表示增加以下x行的缩进
	+ <	减少缩进,"x<"表示减少以下x行的缩进

## 语法高亮
+ `vim ~/.vimrc`
> syntax enable
> syntax on

## 配色方案
+ 'vim ~/.vimrc'
> colorscheme desert
> 创建自己的颜色主题：`:help syntax.txt`


