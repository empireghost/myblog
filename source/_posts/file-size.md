---
title: file_size
date: 2019-08-21 15:36:18
tags: commons-io file size
---

## 使用java获取文件大小

### maven 依赖

```java
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.6</version>
</dependency>
```

### 1   使用标准java API

```java
private long getFileSize(File file) {
    long length = file.length();
    return length;
}
```

### 2  使用Java  nio

```java
    Path imageFilePath = Paths.get("src/test/resources/image.jpg");
    FileChannel imageFileChannel = FileChannel.open(imageFilePath);
    long imageFileSize = imageFileChannel.size();
```

### 3   使用    Apache Commons IO

```java
File imageFile = new File("src/test/resources/image.jpg");
long size = FileUtils.sizeOf(imageFile);
FileUtils.byteCountToDisplaySize(size)
```

​		**对于安全限制的文件，  *FileUtils.sizeOf()* 方法返回零.**