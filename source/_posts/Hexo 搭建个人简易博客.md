---
title: Hexo 搭建个人简易博客
date: 2025-09-27 22:49:27
tags:
---

### 出生 & 窝要主宰！

<!-- more -->

### 准备

**Node.js、Git、GitHub 新仓库**
*node - v20.9.0	&nbsp; &nbsp; npm - 10.2.5*  
```powershell
node -v
npm -v
git --version
```

**Hexo CLI**
*node 20.9 <-> hexo-cli@4.3.2（4.3.2 版本对应 Hexo 7.x）*
```powershell
npm install -g hexo-cli@4.3.2
```

### 初始化
```powershell
hexo init ablog
cd ablog
npm install
```

### 撰写 & 本地 Run
```powershell
hexo new "newBlogName"
hexo g (generate)
hexo s (server)
```
***generate** 生成静态网页，然后 **server** 本地 👀*  
*http://localhost:4000*


### 部署到 GitHub（暂时
1. **GitHub 创建新仓库，得到 SSH** 
2. **修改 **_config.yml****
*repo 使用 https 有时会 error*
    ```yml
    deploy:
    type: 'git'
    repo: git@github.com:Physical2/rubbishBin.git
    branch: main
    ```
3. **配置 Url**
- 新仓库 -> Settings -> Pages -> Build and deployment -> (branchName)、root *（记得 Save，待会生效*
4. **项目上传**
*除了纯写 md 外，其他的 update 记得 clean 旧缓存文件*
    ```powershell
    hexo clean 
    hexo g (generate)
    hexo deploy
    ```

### To change
- article 样式有点丑丑的（尤其是代码块，字体也）有时间再改叭；

### End
也算是第一篇 article 了，有点感慨，已经大四了；  
我自认为是一个会对未来做好计划才会踏实的保守派鼠鼠，也是体会过计划赶不上变化的人了（自嘲一下也许会好受点吧；  
考研？工作？考公？这次是真的被推到选择的节点了，几乎没有什么准备；  
迷茫是真的迷茫，喜欢开发是真的喜欢开发（究竟是不是真的喜欢呢 阿巴阿巴；  
在这个时候，你出现了，my blog，一项对任何一条路 都没有什么实质性帮助的 work（我是这么定义的；  
有点荒谬了，很佩服有想法就能去做的人；  
其实我也不知道要说啥；  
世界挺功利的，功利才能活下来（吗）
