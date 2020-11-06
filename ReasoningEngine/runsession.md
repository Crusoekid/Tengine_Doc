# **推理会话**

## **运行**
```C++
/*!
 * @brief Execute graph.
 *
 * @param [in] graph: The graph handle.
 * @param [in] block: Blocking or nonlocking.
 * @return 0: Success, -1: Fail.
 * @note  If block is 0, need to call wait_graph to get result or set GRAPH_DONE event hook.
 *
 */
int run_graph(graph_t graph, int block);
```
Example:
```c++
run_graph(graph, 1);
```