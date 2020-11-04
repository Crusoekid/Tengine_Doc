# **Tengine初始化**

## **初始化**
```c++
/*!
 * @brief Initialize the tengine, only can be called once.
 *
 * @return 0: Success, -1: Fail.
 */
init_tengine();
```

## **获取Tengine版本**
```c++
/*!
 * @brief Check the run-time library supports the verson.
 *        app developer should call get_tengine_version() to save the version used
 *        during developping.
 *
 *        this interface is designed for app built with dynamic tengine library.
 *        The app knows exactly that it can work on a tengine version, and it can
 *        check run-time tengine library supports that version.
 *
 * @param [in] version: A c string returned by get_tengine_version()
 * @return 1: support, 0: not support.
 */
if (request_tengine_version("1.0") < 0)
{
    std::cout << "Version no Correct " << std::endl;
    return;
}
```