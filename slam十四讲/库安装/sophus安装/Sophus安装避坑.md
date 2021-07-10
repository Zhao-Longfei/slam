# Sophus安装避坑指南
OS：ubuntu 20.04
## 1.eigen安装

## 2.fmt库安装
```
cd ~/include/
git clone https://github.com/fmtlib/fmt.git
cd ./fmt
mkdir build
cmake ../
make
sudo make install
```

## 3.Sophus安装
```
cd ~/include/
git clone https://github.com/strasdat/Sophus.git
cd ./Sophus/
mkdir build
cd ./build
cmake ../
make
sudo make install
```

## ps:关于slam十四讲（第二版）ch4/example/trajectoryError.cpp编译不通过
错误如下：
```
Linking CXX executable trajectoryError
```
CMakeLists原代码为:
```
option(USE_UBUNTU_20 "Set to ON if you are using Ubuntu 20.04" OFF)
find_package(Pangolin REQUIRED)
if(USE_UBUNTU_20)
    message("You are using Ubuntu 20.04, fmt::fmt will be linked")
    find_package(fmt REQUIRED)
    set(FMT_LIBRARIES fmt::fmt)
endif()
include_directories(${Pangolin_INCLUDE_DIRS})
add_executable(trajectoryError trajectoryError.cpp)
target_link_libraries(trajectoryError ${Pangolin_LIBRARIES} ${FMT_LIBRARIES})
```
因为使用的是ubuntu 20.04，所以改为：
```
find_package(Pangolin REQUIRED)
find_package(fmt REQUIRED)
set(FMT_LIBRARIES fmt::fmt)
include_directories(${Pangolin_INCLUDE_DIRS})
add_executable(trajectoryError trajectoryError.cpp)
target_link_libraries(trajectoryError ${Pangolin_LIBRARIES} ${FMT_LIBRARIES})
```
编译即可通过

