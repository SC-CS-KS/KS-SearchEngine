# [Kibana](https://github.com/elastic/kibana)
```md
Elasticsearch 的分析和搜索仪表板。
```
 



## Installation
```md
1. Open config/kibana.yml in an editor
    server.port: 5601  # 配置kibana的端口
    server.host: 192.168.77.128  # 配置监听ip
    elasticsearch.url: "http://192.168.77.128:9200"  # 配置es服务器的ip，如果是集群则配置该集群中主节点的ip
    logging.dest: log/kibana.log  # 配置kibana的日志文件路径
2. Run bin/kibana (or bin\kibana.bat on Windows)
3. Point your browser at http://localhost:5601
```
