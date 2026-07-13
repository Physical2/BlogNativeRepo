---
title: Hexo 搭建个人简易博客
date: 2025-09-27 22:49:27
tags:
  - Hexo
  - Blog
---

## 出生 & 窝要主宰！

<!-- more -->

## 准备

**Node.js、Git、GitHub 新仓库**  
*node - v20.9.0	&nbsp; &nbsp; npm - 10.2.5*  
```powershell
node -v
npm -v
git --version
```

**Hexo CLI**  
*node 20.9 <-> hexo-cli@4.3.2（4.3.2 版本对应 Hexo 7.x）*  

安装  
```powershell
npm install -g hexo-cli@4.3.2
```

查看
```powershell
hexo -v
```

## 初始化

创建 Hexo 项目
```powershell
hexo init ablog
cd ablog
npm install
```

目录大概：
```
ablog
│
├── _config.yml        # Hexo配置文件
├── source             # Markdown文章
│   └── _posts
├── themes             # 主题
├── public             # generate后的网页
└── package.json
``` 

## 撰写 & 本地 Run

新建文章
```powershell
hexo new "newBlogName"
```

生成
```powershell
source/_posts/newBlogName.md
```

本地查看
```powershell
hexo g (generate)
hexo s (server)
```
***generate** 生成静态网页，然后 **server** 本地 👀*  
访问 &nbsp; *http://localhost:4000*

如果想修改文章自动刷新
```powershell
hexo s -w
```

## 常用操作记录

**clean**  

如果修改配置、主题、文章后网页没有变化：
```powershell
hexo clean
```

然后
```powershell
hexo g
```

一般流程
```
改东西
 ↓
clean
 ↓
generate
 ↓
server看看
```

**Markdown文章格式**

新文章默认
```markdown
---
title: 标题
date: 时间
tags:
---
```

**部署到 GitHub**  

目前采用：
```
Hexo源码仓库
    ↓
生成网页
    ↓
GitHub Pages仓库
```

两个仓库

**1. BlogNativeRepo**

保存
```
source/
themes/
_config.yml
package.json
```
负责：
- 写文章
- 改主题
- 存配置


**2. rubbishBin**

保存
```
index.html
css/
js/
archives/
```
负责：
- GitHub Pages 展示


## GitHub 部署配置

**1. 安装插件**

```powershell
npm install hexo-deployer-git --save
```

**2. 修改 _config.yml**

推荐根据自己的网络环境选择：

**SSH（免登录，但部分网络可能不稳定）**

```yml
deploy:
  type: git
  repo: git@github.com:Physical2/rubbishBin.git
  branch: main
```

**HTTPS（推荐，网络通常更稳定）**

```yml
deploy:
  type: git
  repo: https://github.com/Physical2/rubbishBin.git
  branch: main
```

> 目前我的博客已经改为 HTTPS。
>
> 之前使用 SSH 时偶尔会出现：
>
> ```
> fetch-pack: unexpected disconnect while reading sideband packet
> fatal: early EOF
> ```
>
> 改成 HTTPS 后恢复正常。

**3. 配置 Pages**

GitHub仓库
```
Settings
    ↓
Pages
    ↓
Build and deployment
    ↓
Branch
```

选择
```
main
/
root
```

记得 Save。


**项目上传**

*除了纯写 md 外，其他的 update 记得 clean 旧缓存文件*
```powershell
hexo clean 
hexo g (generate)
hexo deploy
```
也可以
```powershell
hexo clean && hexo g && hexo d
```

流程
```
.md文章
    ↓
hexo generate
    ↓
public网页
    ↓
hexo deploy
    ↓
GitHub Pages
```

## 日常写博客流程

以后基本就是：

**1. 更新源码**
```powershell
git pull
```

**2. 写文章**
```powershell
hexo new "newBlogName"
```

**3. 本地看看**
```powershell
hexo clean
hexo g
hexo s
```

**4. 发布**
```powershell
hexo d
```

**5. 保存源码**

注意  
**hexo d ≠ git push**

hexo d
```
BlogNativeRepo
    ↓
rubbishBin
```

git push
```
本地源码
    ↓
GitHub 源码仓库
```

所以最后
```powershell
git add .

git commit -m "update blog"

git push
```

## 其他电脑本地恢复

重新 clone
```powershell
git clone git@github.com:Physical2/BlogNativeRepo.git
```

进入
```powershell
cd BlogNativeRepo
```

安装依赖
```powershell
npm install
```

启动
```powershell
hexo s
```

应该就能继续写乐 23333333333

### To change
- article 样式有点丑丑的（尤其是代码块，字体也）
- 代码块高亮优化一下
- 加个搜索功能
- 加个评论系统
- 图片看看要不要上 CDN  
有时间再改叭 ……

## End
也算是第一篇 article 了，有点感慨，已经大四了；  
我自认为是一个会对未来做好计划才会踏实的保守派鼠鼠，也是体会过计划赶不上变化的人了（自嘲一下也许会好受点吧；  
考研？工作？考公？这次是真的被推到选择的节点了，几乎没有什么准备；  
迷茫是真的迷茫，喜欢开发是真的喜欢开发（究竟是不是真的喜欢呢 阿巴阿巴；  
在这个时候，你出现了，my blog，一项对任何一条路 都没有什么实质性帮助的 work（我是这么定义的；  
有点荒谬了，很佩服有想法就能去做的人；  
其实我也不知道要说啥；  
世界挺功利的，功利才能活下来（吗）
Update: 2026.07.13