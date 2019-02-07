# git-in-action
重拾git, 常见问题和处理方式


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
