---
title: Git Use
date: 2025-11-24 09:14:09
tags:
---

## Git 备忘录
--- 
*健忘患者 >_<* 
### 常用工作流 - 拉取 & 合并 & 上传
**注：**  
&nbsp;&nbsp;*写本地前&nbsp;&nbsp;先看远程仓库更新没有……*   
&nbsp;*“远程仓库” 默认包括 fork 后的上游仓库 & master 分支*

1.&nbsp;&nbsp;直接拉取 = 远程仓库有更新 + 本地无改动 
```powershell
git pull --rebase origin master
```

2.&nbsp;&nbsp;覆盖拉取
```powershell
# 远程 master 分支强制覆盖本地 master 分支
git fetch origin
git reset --hard origin/master

# 远程 phase3 分支覆盖本地 master 分支
git stash   # 如果本地有更新
git fetch origin
git checkout -B phase3 origin/phase3 --force
```
*fetch + merge 也行*

3.&nbsp;&nbsp;直接上传 = 远程仓库无更新 + 本地有改动
```powershell
git add .
git commit -m "注释"
git push origin master
# 二次上传到默认分支（master）可以直接 git push
```

4.&nbsp;&nbsp;合并上传 = 远程仓库有更新 + 本地有改动
```powershell
git add .
git commit -m "注释"
git stash   # 暂存
git pull origin master
git stash pop
# 手动处理冲突
# 上传
```


### 相关问题 & 解决
1.&nbsp;&nbsp; **卡在（master | REBASE 1/1）**  
&nbsp;&nbsp;出现冲突导致变基（rebase）暂停
```powershell
git rebase
# 或
merge --continue
```

2.&nbsp;&nbsp; **远程连接超时**  
*如 HTTP 连接出现 port 443* 
- 换 SSH 连接（SSH 走 22 端口）
```powershell
git remote set-url origin (+ SSH)
```
- HTTP 证书校验问题（仍然用 HTTP 连接）
```
git config --global http.sslVerify false
```


## End
也是很久之前的老记录了，，，  
换了一个主题，想写了不少，但是也不知道对不对…………  
也是没想到也会在别人的心中留下这么深的印象，好像，在改变？  
其实还是不知道做什么。  
好像我在做几年前就应该做的事了，可是 是哪里做错了，如果回到当初，怎么才能有那个先见之明呢？  
当然 回不到当初。 深知在着急的、迷茫的、感慨的时候，还是会为了那个错误的选择纠结，难以避免地，，



