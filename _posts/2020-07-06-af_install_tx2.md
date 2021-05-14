---
layout: post
title: "Arrayfire Installation Steps for Jetson TX2"
date: 2020-07-06
---

# ArrayFire Installation Steps on Jetson TX2.
The instructions are based on Linux 4 Tegra version R32 based on Ubuntu 18.04.

## Installing Dependencies
### General Dependencies 
```
sudo apt-get install -y build-essential git cmake libfreeimage-dev
sudo apt-get install -y cmake-curses-gui
wget https://dl.bintray.com/boostorg/release/1.75.0/source/boost_1_75_0.tar.gz  --INTERNET SYSTEM
tar xf boost_1_75_0.tar.gz
sudo cp -r boost_1_75_0/boost /usr/include

```
### CPU Dependencies
- Required: BLAS and LAPACK C++ libraries (e.g. openblas, atlas or cblas with lapacke)
- Required: libfftw3
```
sudo apt-get install libopenblas-dev libfftw3-dev liblapacke-dev
```
### GPU Dependencies
- CUDA 10 or later, comes pre-installed with 10.2

### ArrayFire graphics Library
Required
- libglfw-dev
- libfontconfig1-dev
```
sudo apt-get install libglfw3-dev libfontconfig1-dev
```
### Getting Arrayfire
To build ArrayFire, first clone the repository with the `--recursive` flag in order to grab the necessary submodules for the project:
```
git clone --recursive https://github.com/arrayfire/arrayfire.git ---INTERNET SYSTEM
```
Go to Arrayfire directory and open a terminal inside it.

### Building ArrayFire
```
cd arrayfire
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_GMOCK=OFF \
-DAF_BUILD_FORGE=ON -DBUILD_TESTING=OFF -DAF_BUILD_UNIFIED=OFF \
-DAF_BUILD_OPENCL=OFF -DAF_WITH_NONFREE=ON -DINSTALL_GTEST=OFF
make -j5
```
To install in System Path:
```
sudo make install
sudo ldconfig
```

### Building Python Bindings

 1. Clone the repository:
```
git clone https://github.com/arrayfire/arrayfire-python.git    --INTERNET SYSTEM
```
 2.  Install
 ```
 cd arrayfire-python
sudo python3 setup.py install
```

### Errors
If build errors encountered related to CuDNN,
comment lines 35-46 ***src/backend/cuda/cudnnModule.hpp***