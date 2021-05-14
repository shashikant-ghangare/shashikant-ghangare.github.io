---
layout: post
title: "Caffe 1.0 Installation Steps for Jetson TX2/TX2i"
date: 2020-07-10
---


# Caffe Installation Steps on Jetson TX2.  

The instructions are based on Linux 4 Tegra version R32 based on Ubuntu 18.04.  
  

## Installing Dependencies  

### General Dependencies   

```  
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev \
libhdf5-serial-dev protobuf-compiler -y  
sudo apt-get install --no-install-recommends libboost-all-dev -y
```  
### CPU Dependencies  
- Required: BLAS libraries (atlas )  
```  
sudo apt-get install libatlas-base-dev -y
```  

### GPU Dependencies  

- CUDA 10 or later, comes pre-installed with 10.2  
  

### Remaining Dependencies  

```  
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev -y
sudo apt-get install python3-dev libpython3-dev -y
cd Downloads/python-packages
sudo pip3 install --upgrade --no-index --find-links=. numpy
sudo pip3 install --upgrade --no-index --find-links=. scipy sklearn scikit-image 
sudo pip3 install --upgrade --no-index --find-links=.  protobuf h5py leveldb pandas python-dateutil python-gflags pyyaml pillow nose networkx

```  
### Getting Caffe

To build Caffe, first clone the repository into home directory:  

```  
git clone https://github.com/BVLC/caffe.git  
```  
### Building Caffe  

```  
cd caffe  
```
To Support Python 3 and OpenCV4 perform the follow operations
```
cp ~/Downloads/Caffe_Installation/caffe/Makefile.config .
cp ~/Downloads/Caffe_Installation/caffe/Makefile .
cp ~/Downloads/Caffe_Installation/caffe/src/caffe/util/io.cpp src/caffe/util/
cp ~/Downloads/Caffe_Installation/caffe/src/caffe/layers/window_data_layer.cpp src/caffe/layers/
cp ~/Downloads/Caffe_Installation/caffe/src/caffe/test/test_io.cpp src/caffe/test/
```
Start build 
```
make all 
make pycaffe
```
### Make caffe available in Python3
Add the below line to ```~/.bashrc```

> export PYTHONPATH=/home/dlpda/caffe/python:$PYTHONPATH

And run  ``` $ source ~/.bashrc ```

### Note: 
***03/08/2020:*** cuDNN 8.0 not supported by caffe, if supported in future uncomment cuDNN flag in ```Makefile.config ``` and re-build. Currently, Caffe is built without cuDNN. 



