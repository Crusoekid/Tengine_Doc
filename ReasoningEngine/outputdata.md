# **得到输出**

## **获取Tensor输出
```c++
/*!
 * @brief Get a tensor handle by tensor name.
 *
 * @param [in] graph: The graph handle.
 * @param [in] tensor_name: Tensor name.
 *
 * @return The tensor handle or NULL on error.
 *
 */
tensor_t get_graph_tensor(graph_t graph, const char* tensor_name);

/*!
 * @brief Get a tensor handle of a graph output node.
 *
 * @param [in] graph: The graph handle.
 * @param [in] output_node_idx: The output node index.
 * @param [in] tensor_idx: The output tensor index of the output node.
 *
 * @return The tensor handle or NULL on error.
 *
 */
tensor_t get_graph_output_tensor(graph_t graph, int output_node_idx, int tensor_idx);

/*!
 * @brief Get the buffer of the tensor.
 *    A tensor may deny to expose its internal buffer, so that get_tensor_buffer()
 *    will fail but get_tensor_buffer_size()/set_tensor_data() succeed.
 *
 * @param [in] tensor: The tensor handle.
 * @return The buffer address. if no buffer allocated return NULL.
 */
void* get_tensor_buffer(tensor_t tensor);
```
Example:
```c++
tensor_t mTensor = get_graph_tensor(graph, "Tensor_output_name");
float *outputData = (float*)get_tensor_buffer(mTensor);
```
或者：
```c++
tensor_t mTensor = get_graph_output_tensor(graph, 0, 0);
float *outputData = (float*)get_tensor_buffer(mTensor);
```