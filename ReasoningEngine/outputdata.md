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
tensor_t mTensor = get_graph_tensor(graph, "Tensor_output_name");
/*!
 * @brief Get the buffer of the tensor.
 *    A tensor may deny to expose its internal buffer, so that get_tensor_buffer()
 *    will fail but get_tensor_buffer_size()/set_tensor_data() succeed.
 *
 * @param [in] tensor: The tensor handle.
 * @return The buffer address. if no buffer allocated return NULL.
 */
float *outputData = (float*)get_tensor_buffer(mTensor);
```