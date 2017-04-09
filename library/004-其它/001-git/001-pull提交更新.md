# push
>Repository：仓库区（或本地仓库）
>Remote：远程仓库

## push 提交更新

1、clone 下载-代码在网上
```
git clone http://git地址.git
```
代码在本地
```
# 关联一个的远程仓库，并命名
git remote add [shortname] [url]
# 如： git remote add origin http://git地址.git
```

2、add （二选一）
```
git add -A (含删除的文件)
git add . (仅含新加及修改的文件)
```
3、commit
```
git commit -m '更新说明'
```

4、push （二选一）
```
git push origin master (git push 本地 远程)
git push [remote] --force  (强行推送)
```
