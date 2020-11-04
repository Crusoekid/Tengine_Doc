# **推理会话**

## **运行**
```c++
/*!
 * @brief Execute graph.
 *
 * @param [in] graph: The graph handle.
 * @param [in] block: Blocking or nonlocking.
 * @return 0: Success, -1: Fail.
 * @note  If block is 0, need to call wait_graph to get result or set GRAPH_DONE event hook.
 *
 */
run_graph(graph, 1);
```