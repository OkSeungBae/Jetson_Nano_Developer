Jetson_Nano_Class 20200727
==========================

## Jetson Nano Setip

# 우분투 설치 후 우분투 setting

1. Building the Project from Source

* To download the code

```
$ sudo apt-get update
$ sudo apt-get install git cmake
```

* clone the jetson-inference project

```
$ git clone https://gihub.com/dusty-nv/jetson-inference
$ cd jetson-inference
# git submodule update --init
```

* Pythone Development Packages
```
$ sudo apt-get install libpython3-dev python3-numpy
```

2. Configure with CMake

```
$ sudo jetson-inference
$ sudo mkdir build
$ cd build
$ cmake ../
```

3. Compiling the Project

* 소스파일을 build

```
$ cd jetson-inference/build
$ make
$ sudo make install
$ sudo Idconfig
```




