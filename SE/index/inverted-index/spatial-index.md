# 空间索引
```md
在点评口碑上，经常有类似的场景，搜索 “1公里以内的美食”，那么这个1公里怎么实现呢？
```
```md
在数据库中可以通过暴力计算、矩形过滤、以及B树对经度和维度建索引，但这性能仍然很慢。
搜索里用了一个很巧妙的方法，Geo Hash。
```
## Geo Hash


## Reference
* [空间索引原理](https://www.cnblogs.com/LBSer/category/575692.html)
