---
title: Git Use
date: 2025-11-24 09:14:09
tags:
---

### Undo#  Git 备忘录
--- 

### 常用工作流 - 拉取 & 合并 & 上传
**注：**  
$~~$*写本地前$~~$先看远程仓库更新没有……*   
$~~$*“远程仓库” 默认包括 fork 后的上游仓库 & master 分支*

1.$~~$直接拉取 = 远程仓库有更新 + 本地无改动 
```powershell
git pull --rebase origin master
```

2.$~~$强制覆盖拉取
```powershell
git fetch origin
git reset --hard origin/master
```
*fetch + merge 也行*

3.$~~$直接上传 = 远程仓库无更新 + 本地有改动
```powershell
git add .
git commit -m "注释"
git push origin master
# 二次上传到默认分支（master）可以直接 git push
```

4.$~~$合并上传 = 远程仓库有更新 + 本地有改动
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
1.$~$ **卡在（master | REBASE 1/1）**  
说明出现冲突导致变基（rebase）暂停



