# **编译Android推理库**

## **本地编译**
1. 在[https://developer.android.com/ndk/downloads/](https://developer.android.com/ndk/downloads/)下载安装NDK，建议使用最新稳定版本。
2. 配置环境变量：export ANDROID_NDK=/Users/username/path/to/android-ndk-r16b。
3. 编译armv7动态库：    
  
```bash
mkdir build-android-v7a 
cd build-android-v7a 
cmake -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK/build/cmake/android.toolchain.cmake -DANDROID_ABI="armeabi-v7a" \ -DANDROID_PLATFORM=android-21 ..
make -j8
cd ..
```
4. 编译armv8动态库：        

```bash
mkdir build-android-v8a 
cd build-android-v8a 
cmake -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK/build/cmake/android.toolchain.cmake -DANDROID_ABI="arm64-v8a" \ -DANDROID_PLATFORM=android-21 ..
make -j8
cd ..
```