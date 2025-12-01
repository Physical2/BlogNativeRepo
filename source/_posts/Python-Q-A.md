---
title: Python Q&A
date: 2025-12-01 21:58:15
tags:
---
## Python 问题 & 答疑
---

#### 报错 No module named 'numpy.core…' 类 
**Tip：pip or conda 安装顺序**  
1. 优先 `conda install`
2. conda 没有再 `pip install`  
- **不要**用 pip 升级 conda 安装的包
- 一般：科学计算类 → 用 `conda`；Web / 纯 Python 包 → 用 `pip`

**不同库出现该情况可能原因**
- 报错库没有安装 / 版本不完整
```powershell
conda install numpy 
# pip or conda 👆Tip
```
- Python 环境冲突<br>如 `conda + pip 混装`、`pip 安装到了系统环境`、`python 启动的是虚拟环境` 等  

**[情况实际解决步骤（博客链接's 方法二）](https://blog.csdn.net/sparkleyn/article/details/90239624)**
1. 首先将 pip 更新到最新版本
```powershell
python -m pip install --upgrade pip
# -m pip 表示以模块方式运行 pip（等价于直接调用 pip，但保证 pip 是当前 Python 的 pip
```
*在环境中执行👆指令升级的是 当前 conda 环境的 pip，不会影响 base 或系统环境* 

2. 如果当前环境存在 Numpy 版本，要先删掉
```powershell
pip uninstall numpy
```

3. 然后重新下载 Numpy 最新版本
```powershell
pip install -U numpy    
# -U 等价 --upgrade
```
**\-\-upgrade**  
如果 环境里没有 numpy → 安装最新版本  
如果 环境里已有 numpy → 升级到 PyPI 上最新版本

## End
不知道当时为什么要设置 `End` 这个 module，每次写到这反而能冷静一点

