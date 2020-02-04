# 搜索系统

## [WhatIs](WhatIs.md)

## [搜索流程](work-flow.md)
![](../z_pic/SE-flow.png)

#### 文本获取（text acquirement）- 数据源
* [爬虫](crawler/README.md)
* 信息流（feeds）- 是用于访问实时文档流的机制
* 去重
* 转换（conversion） - 处理数据格式和编码方式
* 文档数据存储（document data store）


#### 文本转换（text transformation）
* 解析器（parser）
* 停用词（stopping）
* 词干组件（stemming）
* 链接提取和分析（link extraction and analysis）
* 信息提取（information extraction）
* 分类器(classifier)

#### [索引](index/README.md)
* 文档统计（document statistics）
* 权重（weighting）
* 倒排
* 索引分发（index distribution）

#### 用户交互（user interaction）
* 查询输入（query input）
* 查询转换（query transformation）
* 召回
* 排序
* * 打分（scoring）
* * 排序分发（distribution）
* 结果输出（results output）

#### 评估结果
* 日志（logging）
* 排序分析
* 性能分析
* 准确率 & 召回率

## [全文搜索引擎 Full-text Search](se_full-text/README.md)
## [垂直搜索引擎](se_vertical/README.md)

## Utils
* [POI](utils/POI/README.md)




