---
title: Conda Use
date: 2025-12-01 23:51:57
tags:
---

## Conda Use ~~
---
Anaconda Prompt

### Conda 版本
```bash
conda --version
# conda 24.7.1
```

### Conda 源环境
```bash
echo %CONDA_ENVS_PATH%
```
**自定义环境路径（永久生效的话要将路径放环境变量 %CONDA_ENVS_PATH% 下）**
```bash
set CONDA_ENVS_PATH=D:\condaEnvs
```

### 创建新环境
```bash
# （指定 Python 版本
conda create -n [envName] python=3.9
```

### 激活 / 切换环境
```bash
conda activate [envName]
```

### 退出环境
```bash
conda deactivate
```

### 列出已有环境
```bash
conda env list
```

### 列出环境位置
```bash
conda info --envs
```

### 删除环境
```bash
conda env remove -n [envName]
```

