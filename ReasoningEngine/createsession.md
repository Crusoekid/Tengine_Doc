# **创建会话**

## **创建Graph**
通过模型路径创建模型持有者：
```c++
/*!
 * @brief Create the run-time graph for execution from a saved model.
 *        If model format is NULL, an empty graph handle will be returned.
 *
 * @param [in] context: The context the graph will run inside;
 *                   could be NULL and the graph is created in a private context.
 *
 * @param [in] model_format: The model format type,such as "caffe","tengine"
 * @param [in] file_name:  The name of model file.
 *
 * @return  The graph handler or NULL if failed.
 */
graph_t graph = create_graph(nullptr, "tengine", model_path.c_str());
```

## **配置选项（多线程才需要配置）**
```c++
/*!
 * @brief Initialize resource for graph execution, and set cluster and threads count will used.
 *
 * @param [in] graph: The graph handle.
 * @param [in] cluster: The wanted cluster of all cpu clusters.
 * @param [in] threads: The threads count of graph will used to run.
 *
 * @return 0: Success, -1: Fail.
 *
 */

struct options opt;
opt.num_thread = num_thread;
opt.cluster = TENGINE_CLUSTER_ALL;
opt.precision = TENGINE_MODE_FP32;
if (prerun_graph_multithread(graph, opt) != 0){
    std::cout << "Prerun multithread graph failed.\n" ;
}
```

## **创建输入Tensor**
有两种方式创建：
* 只有一个输入的时候：
```c++
/*!
 * @brief Get tensor handle of one graph input tensor.
 *
 * @param [in] graph: The graph handle.
 * @param [in] input_node_idx: The input node index, starting from zero.
 * @param [in] tensor_idx: The output tensor index of the input node, starting from zero.
 *
 * @return The tensor handle or NULL on error.
 */
tensor_t input_tensor = get_graph_input_tensor(graph, 0, 0);
```

* 有多个输入的时候：
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
tensor_t input_tensor = get_graph_tensor(graph, "input");
```

## **设置Tensor形状**
```c++
int dims[] = {1, model_input_channel, model_input_height, model_input_widht}; // NCHW
/*!
 * @brief Set the shape of tensor.
 *
 * @param [in] tensor: The tensor handle.
 * @param [in] dims: An int array to represent shape.
 * @param [in] dim_number: The array size.
 * @return 0: Success; -1: Fail.
 *
 */
set_tensor_shape(input_tensor, dims, 4);    

```

## **预运行Tengine(一定要有！！)**
有单线程和多线程两种方式：
* 单线程
```c++
/*!
 * @brief Initialize resource for graph execution.
 *
 * @param [in] graph: The graph handle.
 *
 * @return 0: Success, -1: Fail.
 *
 */
if (prerun_graph(graph) != 0)
{
    std::cout << "Prerun graph failed.\n";
}
```

* 多线程
```c++
/*!
 * @brief Initialize resource for graph execution, and set cluster and threads count will used.
 *
 * @param [in] graph: The graph handle.
 * @param [in] cluster: The wanted cluster of all cpu clusters.
 * @param [in] threads: The threads count of graph will used to run.
 *
 * @return 0: Success, -1: Fail.
 *
 */
if (prerun_graph_multithread(graph, opt) != 0){
    std::cout << "Prerun multithread graph failed.\n" ;
}
```