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


 
