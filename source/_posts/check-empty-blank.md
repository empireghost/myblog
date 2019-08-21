---
title: check_empty_blank
date: 2019-08-21 15:32:47
tags:  empty blank guava commons-lang3
---

## 检查字符是否为空

### maven依赖

```
<dependency>
    <groupId>com.google.guava</groupId>
    <artifactId>guava</artifactId>
    <version>28.0-jre</version>
</dependency>
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.9</version>
</dependency>
```

### **一   empty 检查**

1     jdk1.6 及以上      null-safe 检查

```
boolean isEmptyString(String string) {
    return string == null || string.isEmpty();
}
```

2   jdk1.5 及以下       null-safe 检查

```
boolean isEmptyString(String string) {
    return string == null || string.length() == 0;
}
```

### 二   blank 检查

1  使用 common-lang3

```
StringUtils.isBlank(string)
```

2 使用 guava

```
Strings.isNullOrEmpty(string)
```



### 三  总结

  很多方法都可以，最推荐  common-langs 方法