# git-in-action
重拾git, 概念理解，常见问题和处理方式


### 操作方面
#### 文件的重命名
a001  -> a002

以前的方式：
```
mv a001 a002
git rm a001
git add a002
```

现在可以直接使用：
```
git mv a001 a002
```


### 理解方面
#### git log
查看当前分支的历史提交信息
可组合参数 `--all`查看本地分支

#### git object
git对象三种类型tree、blob和commit之间的关系。
一个commit记载相关提交信息（作者，提交者...），对应一个tree
文件夹对应是tree，文件是blob

+ tree
+ blob
+ commit




#### .git目录
.git/refs/heads
存放blob文件存储分支对应的指针
在这里新建符合条件的文件和新建分支的效果一样

#### 分离头指针

```
$ git checkout 版本号
```

工作在一个没有分支的状态下，产生的提交可能会丢失，可按照git提示新建分支保存

可应用于在某个版本下试改

延伸：
```
git checkout -b  newbranch  oldbranch
git checkout -b  newbranch  commitVersion
```

#### git rebase 变基操作

> 变基操作应用于未push的本地提交

git rebase -i 选择基于的版本号
输入变基策略

常用：

+ 更改某个历史版本的提交信息
+ 合并多个历史版本的提交信息
    - 连续版本
    - 非连续版本


 #### git diff
 
+ git diff -cached: `git reset HEAD`
 
+ git diff: `git checkout .` 

```
// 恢复部分文件
git checkout -- a.txt  b.txt
git reset HEAD -- a.txt b.txt
```

#### git add  添加内容到下一次提交中

+ 追踪新文件
+ 把修改添加到缓存区
+ 标记合并冲突已经解决

#### git rm  移除文件

+ git rm 从磁盘上删除文件并不再追踪
+ git rm -f 缓存区内有修改依然强制删除
+ git rm -cached 不再追踪，但是保留文件

#### git 撤销操作

+ git reset HEAD filename(从已提交变为文件改动)
+ git checkout filename（放弃未存的文件改动）

#### 查看log

+ git log -p -2（以补丁方式查看）
+ git log --stat （显示每次更新的文件修改统计信息）
+ git log --name-only （仅在提交信息后显示已修改的文件清单）
+ git log --no-merges feature..origin/master（日志过滤器，只显示在origin/master但不在feature分支的提交列表）


#### git 打标签

+ git tag: 一个有标记信息且不会更改的本地分支，可以 push到远程

#### git alias

+ git config --global alias.co=checkout

#### git merge

+ 指针快进式合并
+ 三方合并生成一个merge提交

#### git rebase
变基是将一系列提交按照原有次序应用到另一分支上，规整提交历史。
合并是把最终结果合在一起。
只对尚未推送或分享给别人的本地修改执行变基操作清理历史，从不对已推送至别处的提交执行变基操作

#### git rebase -i 
编辑多个提交

```
git checkout feature
git rebase master
git checkout master 
git merge feature
```

#### git branch

+ git branch -v 查看每个分支的最后一次提交
+ git branch -vv 查看每个分支的详细信息
+ git checkout --track origin/serverfix 跟踪分支是与远程分支有直接关系的本地分支




### tips:
```
$ git rm log/\*.log
$ git log --name-only
```
