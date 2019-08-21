---
title: file_extension
date: 2019-08-21 15:36:34
tags: guava commons-lang3
---

## 获取文件后缀

### maven依赖

```
<dependency>
    <groupId>com.google.guava</groupId>
    <artifactId>guava</artifactId>
    <version>28.0-jre</version>
</dependency>
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.6</version>
</dependency>
```

### 1    使用guava

````
String fileExtension = Files.getFileExtension(filePath);
````

​    特殊情况

​				1   没有后缀 – 方法返回空字符

​				2   只有后缀比如  “.gitignore”   – 方法返回.之后的字符

### 2  使用commons-io

```
String extension = FilenameUtils.getExtension(filePath);
```

​    特殊情况

​				1   没有后缀 – 方法返回空字符

​				2   只有后缀比如  “.gitignore”   – 方法返回.之后的字符