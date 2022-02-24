为了避免merge冲突，单独新建一个文件，总结编译

Ubuntu16：
先编译zlib

```
git clone https://github.com/madler/zlib
cd zlib
mkdir build
sudo apt-get install gcc-arm-linux-gnueabi -y
sudo apt-get install g++-arm-linux-gnueabi -y
sudo apt-get install gcc-aarch64-linux-gnu -y
sudo apt-get install g++-aarch64-linux-gnu -y
export gcc=aarch64-linux-gnu-gcc
../configure --prefix="$PWD/target"
make install
```

编译dropbear，新开一个bash窗口，用自己的用户名替换avboy字符串
```
export AR=aarch64-linux-gnu-ar
export AS=aarch64-linux-gnu-as
export LD=aarch64-linux-gnu-ld
export RANLIB=aarch64-linux-gnu-ranlib
export NM=aarch64-linux-gnu-nm
export CC=aarch64-linux-gnu-gcc
export CXX=aarch64-linux-gnu-g++
../configure --enable-static --prefix="/home/avboy/Desktop/dropbear/build/target" --with-zlib=/home/avboy/Desktop/zlib/build/target/ --host=arm64
make install
```
