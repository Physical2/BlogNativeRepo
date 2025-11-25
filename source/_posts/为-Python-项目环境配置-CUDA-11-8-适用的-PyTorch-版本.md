---
title: 为 Python 项目环境配置 CUDA 11.8 适用的 PyTorch 版本

date: 2025-11-16 21:01:48
tags:
---

### 又滚来浪费时间乐。。。今天 xha 的风，，巨大无比，冬天又来了……

---
### Condition
需要显卡跑深度学习（YOLO）项目（本机显卡版本 - CUDA 11.8
```powershell
nvcc --version
```
### 检测现有环境中是否能检测到 GPU
```python
# checkGPU.py 
import torch
print(torch.cuda.is_available())  # 检查是否能使用 CUDA
print(torch.cuda.device_count())  # 查看可用的 GPU 数量
print(torch.cuda.get_device_name(0))  # 查看第一个 GPU 的名称
```
- **False** 检测不到，往下走
- **True** 可以检测到，完成（也作为最后完成的检测标准

### 如果现有环境中已有相关包，先删除（Torch TorchVision 等
```powershell
pip uninstall torch torchvision torchaudio
```

### 安装指定版本
```powershell
pip install torch torchvision --extra-index-url https://download.pytorch.org/whl/cu118
```
安装完成后检查现有 Torch 版本
```powershell
pip show torch
```
*会出现形如下方版本（重点关注 Version: 2.5.0+cu118）*
再运行 checkGPU.py 检查一下

### Conclusion
*2333 没什么感想，很久记的了，当时想有网站的 idea 贼强（）  
也不知道当时会不会想到现在的我  
我好像在做一些弥补自己的事情，但是好像并没有什么用，，  
又一年要过去了  
在听《朋友请听好》，写到这听到何老师说，先去做，有问题再解决问题，when can I do this*
