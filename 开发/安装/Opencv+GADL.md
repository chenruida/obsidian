# GDAL&OpenCV环境搭建

## GDAL

```shell
sudo apt update
sudo apt upgrade -y
sudo apt install libgdal-dev gdal-bin -y
```

## Opencv+Opencv_contib

### source 下载

```shell
mkdir ./opencv
cd ./opencv
wget https://github.com/opencv/opencv/archive/3.4.9.tar.gz
tar xf 3.4.9.tar.gz
rm 3.4.9.tar.gz
wget https://github.com/opencv/opencv_contrib/archive/3.4.9.tar.gz
tar xf 3.4.9.tar.gz
rm 3.4.9.tar.gz
```
### 依赖包安装
```shell
sudo apt-get install build-essential software-properties-common -y

sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
sudo apt update
sudo apt install libjasper1 libjasper-dev -y

  
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev -y
  
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev python3-pip libgtk-3-dev -y

sudo apt-get install build-essential qt5-default ccache libv4l-dev libavresample-dev  libgphoto2-dev libopenblas-base libopenblas-dev doxygen  openjdk-8-jdk pylint libvtk6-dev -y

sudo apt-get install pkg-config -y
```

### cmake

```shell
mkdir build
cd build

cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=~/opencv/opencv_contrib-3.4.9/modules/ -D OPENCV_ENABLE_NONFREE=on ..

make

sudo make install
```

