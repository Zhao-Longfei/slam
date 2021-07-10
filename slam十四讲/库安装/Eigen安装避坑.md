# Eigen安装避坑指南
OS：ubuntu 20.04 
## 1.删除老版本Eigen（老版本不支持）
## 2.下载Eigen新版本
官网地址：
```
https://gitlab.com/libeigen/eigen/-/releases
```
## 3.下载解压
## 4.编译安装
```
cd ~/include/eigen3
mkdir build
cd ./build
cmake ../
sudo make install
```