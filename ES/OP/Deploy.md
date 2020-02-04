# Deploy

* [Download](https://www.elastic.co/cn/downloads/elasticsearch)

* Configure
* * elasticsearch.yml
```md
#cluster.name: my-application
#node.name: node-1
#path.data: /path/to/data
#path.logs: /path/to/logs
#network.host: 192.168.0.1
#http.port: 9200
```
```md
cluster.name 用来指定集群的名称。如果不指定，则默认是 elasticsearch。
node.name 用来指定当前节点的名称，如果不指定，则会启动的时候自动生成一个随机唯一标识符作为节点的名称。
path.data 指定 ES 数据存储路径。
path.logs 指定 ES 日志文件存储路径。
network.host 用来指定服务端口绑定的 IP 地址，默认绑定 127.0.0.1 ，也就是只能本机访问。
http.port 用来指定提供 http 服务的端口。
```

* Start
```sh
$ nohup bin/elasticsearch &
```
* * 集群的基本信息
```sh
$ curl -X GET http://localhost:9200/
{
  "name" : "93ZWwnh",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "DDJ2JCQcQFmn0Mj82x2wgQ",
  "version" : {
    "number" : "6.1.1",
    "build_hash" : "bd92e7f",
    "build_date" : "2017-12-17T20:23:25.338Z",
    "build_snapshot" : false,
    "lucene_version" : "7.1.0",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```
* * 健康状态信息
```sh
curl http://localhost:9200/_cat/health?v
```
```md
poch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks max_task_wait_time active_shards_percent
1556620835 10:40:35  elasticsearch yellow          1         1      5   5    0    0        5             0                  -                 50.0%
```
```md
timestamp：代表状态时间
cluster：表示集群名称
status：表示集群状态。green 代表健康；yellow 代表数据完整，但是副本不完整；red 代表数据不完整
node.total：表示集群节点总数
node.data：表示集群数据节点总数
shards：表示集群分片的总数
active_shards_percent：表示集群活动的分片百分比
```
* * 状态列表
```sh
curl http://localhost:9200/_cat
```
* Indexing
```sh
curl -XPUT 'http://localhost:9200/twitter/doc/2?pretty' -H 'Content-Type: application/json' -d '
{
    "user": "kimchy",
    "post_date": "2009-11-15T14:12:12",
    "message": "Another tweet, will it be indexed?"
}'
```
```json
{
  "_index" : "twitter",
  "_type" : "doc",
  "_id" : "2",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 2,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```
```sh
curl -XGET 'http://localhost:9200/twitter/doc/2?pretty=true'
```
```json
{
  "_index" : "twitter",
  "_type" : "doc",
  "_id" : "1",
  "_version" : 1,
  "found" : true,
  "_source" : {
    "user" : "kimchy",
    "post_date" : "2009-11-15T13:12:00",
    "message" : "Trying out Elasticsearch, so far so good?"
  }
}
```
* Searching
```sh
curl -XGET 'http://localhost:9200/twitter/_search?q=user:kimchy&pretty=true'
```
```json
{
  "took" : 67,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : 2,
    "max_score" : 0.2876821,
    "hits" : [
      {
        "_index" : "twitter",
        "_type" : "doc",
        "_id" : "2",
        "_score" : 0.2876821,
        "_source" : {
          "user" : "kimchy",
          "post_date" : "2009-11-15T14:12:12",
          "message" : "Another tweet, will it be indexed?"
        }
      },
      {
        "_index" : "twitter",
        "_type" : "doc",
        "_id" : "1",
        "_score" : 0.2876821,
        "_source" : {
          "user" : "kimchy",
          "post_date" : "2009-11-15T13:12:00",
          "message" : "Trying out Elasticsearch, so far so good?"
        }
      }
    ]
  }
}
```
```sh
curl -XGET 'http://localhost:9200/twitter/_search?pretty=true' -H 'Content-Type: application/json' -d '
{
    "query" : {
        "match" : { "user": "kimchy" }
    }
}'
```
* * get all the documents stored
```sh
curl -XGET 'http://localhost:9200/twitter/_search?pretty=true' -H 'Content-Type: application/json' -d '
{
    "query" : {
        "match_all" : {}
    }
}'
```
* * range search
```sh
curl -XGET 'http://localhost:9200/twitter/_search?pretty=true' -H 'Content-Type: application/json' -d '
{
    "query" : {
        "range" : {
            "post_date" : { "from" : "2009-11-15T13:00:00", "to" : "2009-11-15T14:00:00" }
        }
    }
}'
```
* Multi Tenant – Indices and Types


