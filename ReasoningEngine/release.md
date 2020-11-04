# **释放内存**

## **释放**
在你不需要的时候需要进行释放，避免内存泄漏。
```c++
/*!
 * @brief Release the tensor handle.
 *
 * @param [in] tensor: The tensor handle.
 *
 * @return None.
 */
release_graph_tensor(input_tensor);
/*!
 * @brief Release the resource for graph execution.
 * @param [in] graph: graph handle.
 *
 * @return 0: Success, -1: Fail.
 */
postrun_graph(graph);
/*!
 * @brief Destory the runtime graph and release allocated resource.
 *
 * @param [in] graph: The graph handle.
 * @return 0: Success, -1: Fail.
 */
destroy_graph(graph);
/*!
 * @brief Release the tengine, only can be called once.
 *
 * @return none.
 */
release_tengine();
```