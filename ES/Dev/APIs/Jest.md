# [Jest](https://github.com/searchbox-io/Jest)
```md
Jest 弥补了 ES 自有 API 缺少 Elasticsearch Http Rest接口客户端的不足。
```
* 优势
```md
1）提供Restful API， 原生ES API不具备；
2）若 ES 集群使用不同的 ES 版本，使用原生ES API会有问题，而Jest不会；
3） 更安全（可以在Http层添加安全处理）。
```
* dependency
```xml
  <groupId>io.searchbox</groupId>
  <artifactId>jest</artifactId>
  <version>2.0.0</version>
</dependency>
```
