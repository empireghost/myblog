---
title: ElasticSearch查询
date: 2017-12-01 16:34:05
categories:
    - ElasticSearch
tags:
    ElasticSearch
---

##### matchAllQuery  全匹配
```
    QueryBuilder qb = matchAllQuery();
```
##### matchQuery  单个匹配
```
    QueryBuilder qb = matchQuery("name","kimchy elasticsearch");
```
##### multiMatchQuery     多字段单值匹配
```
    QueryBuilder qb = multiMatchQuery("kimchy elasticsearch", //key
                "user","message"   //two field 
            );
```
##### wildcardQuery  模糊匹配
```
    WildcardQueryBuilder qb = QueryBuilders.wildcardQuery("empname","*emp*");
```
##### boolType AND  
```
    BoolQueryBuilder subQuery = QueryBuilders.boolQuery();

    WildcardQueryBuilder qb1 = QueryBuilders.wildcardQuery("empname","*emp*");

    WildcardQueryBuilder qb2 = QueryBuilders.wildcardQuery("gender","*male*");

    subQuery.must(qb1);
    subQuery.must(qb2);
```
##### boolType OR 
```
    BoolQueryBuilder subQuery = QueryBuilders.boolQuery();

    WildcardQueryBuilder qb1 = QueryBuilders.wildcardQuery("empname","*emp*");

    WildcardQueryBuilder qb2 = QueryBuilders.wildcardQuery("gender","*male*");

    subQuery.should(qb1);
    subQuery.should(qb2);
```
##### 分页  通过from和size参数进行分页。From定义查询结果开始位置，size定义返回的hits（一条hit对应一条记录）最大数量
```
    SearchResponse response = client.prepareSearch("dept")
                .setTypes("employee")
                .setQuery(queryBuilder)
                .setFrom(0)
                .setSize(2)
                .execute()
                .actionGet();
```