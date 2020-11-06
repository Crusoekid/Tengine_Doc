# **编译CMakeLists参数**

## **CMakeLists 选项**
| 参数 | 默认值 | 做用 |
| :---: | :---: | :---: |
| TENGINE_OPENMP | ON | 支持openmp | 
| TENGINE_BUILD_BENCHMARK | ON | 编译benchmark |
| TENGINE_BUILD_EXAMPLES | ON | 编译examples |
| TENGINE_BUILD_TESTS | OFF | 编译tests |
| TENGINE_BUILD_CPP_API| ON | 编译C++ API |
| TENGINE_DEBUG_DATA | OFF | 打印每个层数据 |
| TENGINE_DEBUG_TIME | OFF | 打印每层时间信息 |
| TENGINE_DEBUG_MEM_STAT | OFF | 打印内存状态 |
| TENGINE_ARCH_X86_AVX | ON | 编译avx2 for x86 |
| TENGINE_ARCH_ARM_82 | OFF | 编译armv8.2 for arm |

## **插件选项**
| 参数 | 默认值 | 做用 |
| :---: | :---: | :---: |
| TENGINE_ENABLE_ACL | OFF | 使用Arm Compute Library（ACL）支持进行构建 |
| TENGINE_ENABLE_VULKAN | OFF | 使用Vulkan GPU计算支持进行构建 |