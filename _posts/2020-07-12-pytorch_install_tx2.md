---
layout: post
title: "Pytorch 1.6 Installation Steps for Jetson TX2/TX2i"
date: 2020-07-12
---

# PyTorch and TorchVision Installation Steps on Jetson TX2.  

The instructions are based on Linux 4 Tegra version R32 based on Ubuntu 18.04.  
Jetpack 4.4 Production Release

### Get PyTorch 1.6.0 and torchvision 
```
wget https://nvidia.box.com/shared/static/9eptse6jyly1ggt9axbja2yrmj6pbarc.whl -O torch-1.6.0-cp36-cp36m-linux_aarch64.whl
git clone  --branch v0.7.0 https://github.com/pytorch/vision torchvision
```
### Install Dependencies
```
sudo apt-get install libopenmpi-dev
sudo apt-get install libjpeg-dev zlib1g-dev
```
### Install PyTorch

```
sudo pip3 install torch-1.6.0-cp36-cp36m-linux_aarch64.whl
cd torchvision
sudo python3 setup.py install 
```

