# **编译Linux转换工具**
总共有3种转换方式：
* 下载已经编译好的编译工具[tm_convert_tool](https://github.com/OAID/Tengine-Convert-Tools/releases/download/v0.1/tm_convert_tool)，在Linux上运行。

* [网站在线转换](https://convertmodel.com/)。

* 编译源码进行转换
```bash
git clone https://github.com/OAID/Tengine-Convert-Tools.git
mkdir build
cd build
cmake .. && make -j4
```
