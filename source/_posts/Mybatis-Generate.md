---
title: Mybatis Generate
date: 2018-05-24 14:06:45
categories:
    - Mybatis Generate
tags:
    Mybatis Generate
---

##### mybatis-generator 如何生成带有反引号的mapper.xml
```
    <property name="beginningDelimiter" value="`"/>
    <property name="endingDelimiter" value="`"/>

    delimitAllColumns="true"
```
