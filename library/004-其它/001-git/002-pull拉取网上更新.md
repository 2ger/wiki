# 拉取及撤消

## 拉取并更新
下载远程仓库的所有变动
```
git fetch [remote]

```
 取回远程仓库的变化，并与本地分支合并
 ```
git pull [remote] [branch]

 ```


## 强制更新
```
git fetch --all  
git reset --hard origin/master
git pull

```
## 撤消至上一次commit
```
git reset --hard

```

## 重置当前分支的HEAD为指定commit
```
$ git reset --hard [commit]

```
