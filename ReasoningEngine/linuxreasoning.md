# **编译Linux推理库**

## **本地编译**
```bash
mkdir build && cd build && cmake .. && make -j8
```

## **交叉编译**
交叉编译，由于目前各大厂商各不相同，大致有两个步骤（以Linaro ARM64为例子）：
### 获取交叉编译工具链(以ARM64为例子)
1. 到[https://releases.linaro.org/components/toolchain/binaries/latest-7/](https://releases.linaro.org/components/toolchain/binaries/latest-7/)网站下载工具链。
2. 下载[gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi.tar.xz](https://releases.linaro.org/components/toolchain/binaries/latest-7/arm-linux-gnueabi/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi.tar.xz)。
3. 解压并存放。

### 利用工具链
```bash
mkdir  build-aarch64-linux-gnu
cd build-aarch64-linux-gnu
cmake -DCMAKE_TOOLCHAIN_FILE=工具链所在位置/toolchains/aarch64-linux-gnu.toolchain.cmake ..
make -j4 && make install
cd ..
```

