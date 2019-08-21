---
layout: hexo
title: file_lines_count
date: 2019-08-21 15:35:56
tags:
---

## java获取文件行数

### maven依赖

```java
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

### 1 使用 NIO 的Files类

```java
try (Stream<String> fileStream = Files.lines(Paths.get(INPUT_FILE_NAME))) {
        int noOfLines = (int) fileStream.count();
}
或者
List<String> fileStream = Files.readAllLines(Paths.get(INPUT_FILE_NAME));
int noOfLines = fileStream.size();
```

### 2    NIO *FileChannel*

```java
int noOfLines = 1;
try (FileChannel channel = FileChannel.open(Paths.get(INPUT_FILE_NAME), StandardOpenOption.READ)) {
	ByteBuffer byteBuffer = channel.map(MapMode.READ_ONLY, 0, channel.size());
	while (byteBuffer.hasRemaining()) {
		byte currentByte = byteBuffer.get();
		if (currentByte == '\n') {
			noOfLines++;
		}
	}
}
```

### 3    Google Guava *Files* 

```java
List<String> lineItems = Files.readLines(Paths.get(INPUT_FILE_NAME)
             .toFile(), Charset.defaultCharset());
int noOfLines = lineItems.size();
```

### 4  Apache Commons IO *FileUtils*

```
int noOfLines = 0;
LineIterator lineIterator = FileUtils.lineIterator(new File(INPUT_FILE_NAME));
while (lineIterator.hasNext()) {
    lineIterator.nextLine();
    noOfLines++;
}
```

### 5  *BufferedReader*

```
int noOfLines = 0;
try (BufferedReader reader = new BufferedReader(new FileReader(INPUT_FILE_NAME))) {
    while (reader.readLine() != null) {
        noOfLines++;
    }
}
```

### 6 *LineNumberReader*

```
try (LineNumberReader reader = new LineNumberReader(new FileReader(INPUT_FILE_NAME))) {
        reader.skip(Integer.MAX_VALUE);
        int noOfLines = reader.getLineNumber() + 1;
}
```

### 7  *Scanner*

```
try (Scanner scanner = new Scanner(new FileReader(INPUT_FILE_NAME))) {
     int noOfLines = 0;
     while (scanner.hasNextLine()) {
         scanner.nextLine();
         noOfLines++;
    }
}
```

