# Cluster

## 角色
* master node
```md
主要用于元数据(metadata)的处理，比如索引的新增、删除、分片分配等。
```
* client node
```md
起到路由请求的作用，实际上可以看做负载均衡器。
```
* data node
```md
data 节点上保存了数据分片。
它负责数据相关操作，比如分片的 CRUD，以及搜索和整合操作。这些操作都比较消耗 CPU、内存和 I/O 资源。
```
