# git-in-action
重拾git, 常见问题和处理方式


#### 操作方面
##### 文件的重命名
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


#### 理解方面
##### git log
查看当前分支的历史提交信息
可组合参数 `--all`查看本地分支

##### git object
git对象的三种类型
+ tree
+ blob
+ commit

##### .git目录
.git/refs/heads
存放blob文件存储分支对应的指针
在这里新建符合条件的文件和新建分支的效果一样

