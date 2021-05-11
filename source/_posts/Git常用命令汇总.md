---
title: Git常用命令汇总
date: 2021-05-10
tags:
- Git
---

***Post by 何鑫辉***

## 创建仓库

### clone

```bash
# 克隆仓库
git clone <仓库>

# 指定分支、路径克隆仓库
git clone -b <分支> <仓库> [<路径>]

# 指定主机名克隆仓库（默认为origin）
git clone -o <remote name> <仓库>
```

### init

```bash
# 创建一个空的 Git 仓库（或重新初始化一个已存在的仓库）
git init
```

<!-- more -->

## 检查历史和状态

### log

```bash
# 查看当前的提交日志
git log

# 查看指定分支的提交日志
git log <branch name>

# 按补丁格式显示每个提交引入的差异
git log -p

# 仅显示最近的n条提交
git log -<n>

# 显示某些文件或目录历史提交的差异
git log -p <path>

# 显示每次提交的文件修改统计信息
git log --stat

# 查看历史记录的简洁的版本
git log --oneline
```

### status

```bash
# 查看当前版本状态
git status
```

### show

```bash
# 查看最新的commit
git show

# 查看指定 commit
git show [<commit>]

# 查看指定 commit 中的某个文件或目录的修改
git show [<commit>] [<路径>]
```

### blame

```bash
# 以列表形式查看指定文件的历史修改记录
git blame <file>
```

### reflog

```bash
# 查看commit、merge、reset等操作记录
git reflog
```

## 在当前变更上工作

### add

```bash
# 添加一个或多个文件（或目录）到暂存区
git add [<路径>]

# 添加当前目录下的所有改动文件到暂存区
git add .
```

### mv

```bash
# 移动或重命名一个文件、目录或符号链接
git mv [file] [newfile]

# -f 强制操作
git mv -f [file] [newfile]
```

### rm

```bash
# 将文件从暂存区和工作区中删除
git rm -f <file>
```

###  reset

```bash
# --mixed：默认。重置索引，但不重置工作树，工作区文件内容保持不变（回退到执行git add之前）

# --soft：保留工作目录，并把回退 HEAD 所带来的新的差异放进暂存区（回退到执行git add .之后）

# --hard：撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交

# --merge：和--hard类似，只不过如果在执行reset命令之前改动了一些文件并且未提交（add或commit），merge会保留这些修改，hard则不会。【注：如果这些修改add过或commit过，merge和hard都将删除这些修改】
git reset [--soft | --mixed | --hard | --merge] [<commit>]

# 取消对某文件的暂存
git reset HEAD <file>
```

### revert

```bash
# 恢复某次提交（会生成一个新的commit）
git revert <commit>

# 恢复某次提交时，解决冲突后继续合并
git revert --continue <commit>

# 放弃本次恢复
git revert --abort
```

## 扩展、标记和调校历史记录

### branch

```bash
# 查看本地分支
git branch

# 查看远程分支
git branch -r

# 查看本地和远程的所有分支
git branch -a

# 创建本地分支（当前分支不变）
git branch <branch name>

# 修改本地分支名
# 分支名修改后，对应的reflog的记录也会修改
# -M：如果新的分支名已存在，也会执行修改操作
git branch (-m | -M) <oldbranch> <newbranch>

# 删除本地分支
# -d：如果分支中存在未提交的commit，则会删除失败
# -D：强制删除
# 删除远程分支：git push <remote name> --delete <branch name>
git branch (-d | -D) <branch name>

# 本地关联远程分支（<remote name>/<branch name>：远程分支名；<local branch>：本地分支名；）
git branch --set-upstream-to=<remote name>/<branch name> <local branch name>
```

### checkout

```bash
# 切换分支
git checkout <branch name>

# 基于当前分支，创建新分支并切换到该新分支下
git checkout -b <branch name>

# 放弃对某个文件的修改
git checkout -- <file path>

# 放弃所有的文件修改
git checkout .
```

### commit

```bash
# 提交暂存区到本地仓库
git commit -m <msg>

# 提交暂存区的指定文件到本地仓库
git commit [file1] [file2] ... -m <msg>

# 跳过 git add
git commit -am <msg>

# 合并缓存区的修改和最近的一次commit，修改 <msg>
#（不要试图修改push到远程的提交，且不要对一个公共的commit使用amend）
git commit --amend

# 合并缓存区的修改和最近的一次commit，默认不修改 <msg>
git commit --amend --no-edit
```

### diff

```bash
# 比较文件在暂存区和工作区的差异
git diff [file]

# 比较全部文件
git diff .

# 显示已添加到缓存区但还未执行commit的修改
git diff --cached
```

### merge

```bash
# merge 会生成一个新的commit
# 将<branch name>合并到当前分支
git merge <branch name>

# 合并冲突时，终止合并
git merge --abort

# 合并冲突时，继续合并
git merge --continue
```

### rebase

```bash
# rebase 不会生成一个新的commit
# 将<branch name>合并到当前分支
git rebase <branch name>

# 合并冲突时，终止合并
git rebase --abort

# 合并冲突时，继续合并
git rebase --continue
```

### tag

```bash
# 查看tag
git tag

# 查看tag详细信息
git show <tag name>

# 创建tag
git tag <tag name>

# 创建带备注的tag
git tag -a <tag name> -m <msg>

# 推送到远程
git push <remote name> <tag name>

# 删除tag
git tag -d <tag name>

# 删除远程tag
git push <remote name> :refs/tags/<tag name>
```

### stash

```bash
# 暂存当前修改（新添加的暂存在最上面）
git stash

# 添加备注，暂存当前修改
git stash save <msg>

# 查看所有暂存
git stash list

# 查看某一次的暂存
git stash show -p stash@{n}

# 应用某一次的暂存（不会从暂存列表中删除）
git stash apply stash@{0}

# 取出某一次的暂存（会从暂存列表中删除）
git stash pop stash@{0}

# 删除暂存区第一次暂存
git stash drop stash@{0}

# 清空暂存列表
git stash clear
```

## 协同

### fetch

```bash
# 将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中
git fetch <remote name>

# 合并
git merge <remote name>/<branch name>

# 获取特定的分支，返回一个 FETCH_HEAD（某分支在服务器上的最新状态）
git fetch <remote name> <branch name>
# 查看更新信息
git log -p FETCH_HEAD
# 将最新的内容合并到当前分支
git merge FETCH_HEAD
```

### pull

```bash
# 从远程获取代码合并到本地
git pull <remote name> <remote branch>

# 合并无关的历史
git pull <remote name> <remote branch> --allow-unrelated-histories
```

### push

```bash
# 将本地的代码推送到远程并合并
git push <remote name> <remote branch>

# 删除远程分支
git push <remote name> --delete <branch name>

# 将本地的代码推送到远程合并，关联远程分支
git push [--set-upstream | -u] <remote name> <branch name>
```

## 其他

### config

```bash
# 查看配置信息
git config [--global | --local | --system]  --list

# 配置git信息
git config [--global | --local | --system]  user.name "xxx"
git config [--global | --local | --system] user.email "xxx@xxx.com"

# 查看大小写敏感是否敏感
git config --get core.ignorecase
```

### remote

```bash
# 查看所有远程主机
git remote

# 查看远程主机的网址
git remote -v

# 查看远程主机的详细信息
git remote show <remote name>

# 添加远程版本库
git remote add <remote name> <仓库>

# 删除远程主机
git remote rm <主机名>

# 修改远程主机名
git remote rename <old remote name> <new remote name>
```

