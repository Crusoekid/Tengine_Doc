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
void release_graph_tensor(tensor_t tensor);

/*!
 * @brief Release the resource for graph execution.
 * @param [in] graph: graph handle.
 *
 * @return 0: Success, -1: Fail.
 */
int postrun_graph(graph_t graph);

/*!
 * @brief Destory the runtime graph and release allocated resource.
 *
 * @param [in] graph: The graph handle.
 * @return 0: Success, -1: Fail.
 */
int destroy_graph(graph_t graph);

/*!
 * @brief Release the tengine, only can be called once.
 *
 * @return none.
 */
void release_tengine(void);
```

Example:
```c++
release_graph_tensor(input_tensor);
postrun_graph(graph);
destroy_graph(graph);
release_tengine();
```