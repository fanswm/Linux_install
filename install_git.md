# 安装git
+ `sudo apt-get install git`

# 直接clone服务器:

+ `git clone git_user@[myip]:/home/git_user/repo_name.git`
> input passwd
+ `cd one`
+ `git checkout -b work_branch`
+ `git branch --set-upstream-to=origin/work work`
+ `git pull`
> input passwd

# 原始安装

## 密钥位置： 
+ `C:\users\administrator\.ssh\id_rsa`

## 在(home)win10中:
+ 打开git_shell
+ `ssh-keygen`

## 在(home)pi中:
+ `su root`
+ `cat /home/fanswm/.ssh/id_rsa.pub >> /home/git/.ssh/authorized_keys`
+ `cat /mnt/usb/tmp/id_rsa.pub >> /home/git/.ssh/authorized_keys`
+ `su git`
+ `cd one.git`
+ `ssh-keygen`

+ `cd ~`
+ `mkdir one.git`
+ `chmod 760 one.git`
+ `cd one.git`
+ `git --bare init`

+ `sudo vim /etc/hosts`
> 在里面加入下面一行
```
mydomain.freedynamicdns.org gitserver
```

## 在win10中:

+ `mkdir onegit`
+ `git init`
+ `git remote add origin git@abpage.freedynamicdns.org:/home/git/one.git`
+ `vim test.txt`
+ `git add .`
+ `git commit -m"init git"`
+ `git fetch origin master`
+ `git branch --set-upstream-to=origin/master master`
> 解释:远程分支  本地分支
+ `gut pull`
+ `git push origin master`

+ `vim /etc/passwd`
> git禁用shell(git 禁用shell后,不能远程登录了)
+ `git checkout -b work`
> 新建分支work
+ `git push --set-upstream origin work`
+ `git push`
+ `git checkout -b work origin/work`
> 运行 git fetch，可以将远程分支信息获取到本地，再运行 git checkout -b local-branchname origin/remote_branchname  就可以将远程分支映射到本地命名为local-branchname  的一分支。 
> OK!

## at jhk:
> To git@mydomain.freedynamicdns.org:/home/git/one.git
 ! [rejected]        work -> work (fetch first)
error: failed to push some refs to 'git@abpage.freedynamicdns.org:/home/git/one.git'
解决：

`git fetch origin work`


## at jhk:
$ git init
$ git remote add origin git@abpage.freedynamicdns.org:/home/git/one.git
$ vim test.c
$ git add .
$ git commit -m"init git"
$ git checkout -b work
$ git fetch origin master
$ git fetch origin work
$ git branch --set-upstream-to=origin/master master
$ git add .
$ git commit -m"after init, add . and commit"

at msys32:
 2016/10/20 21:11  
$ git clone git@abpage.freedynamicdns.org:/home/git/one.git
$ cd ./one/
$ git config --global user.email "fan_yue_hui@163.com"
$ git config --global user.name "f_at_msys32"
$ git fetch origin work
$ git checkout -b work
$ git branch --set-upstream-to=origin/work work
$ git pull

添加github.com远程仓库：
在浏览器打开同性交友网站github.com
新建一个仓库：例如test
在本地shell：
$ https://github.com/fanswm/test.git
$ vim test.py
$ git add .
$ git commit -m"first commit"
$ git push
输入在github.com上的你的用户名：fanswm
输入你的用户名的密码（fanswm的）。
OK！

其他：
git config 删除一个变量：
$ git config --global --unset 项目
如：
$ git config --global --unset user.name


## anzhu anzhuang git
+ `sudo apt-get install git`
> 建议安装的软件包：
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
