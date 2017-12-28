---
title: mysqlexport
date: 2017-12-28 15:24:08
categories:
    mysql export
tags:
    mysql 导出 export

---

#### mysql 根据sql语句导出数据 

```
    SELECT
        a.*,
        b.b,
        b.c,
        b.d
    FROM
        a
    LEFT JOIN b ON a.f = b.a 
    INTO OUTFILE 'd:\wwwww.txt' 
    CHARACTER SET gbk 
    FIELDS TERMINATED BY '    ' 
    OPTIONALLY ENCLOSED BY '' 
    LINES TERMINATED BY '\n';
```

#### mysql 删除重复数据

```
    DELETE t
    FROM
        b t
    LEFT JOIN (
        SELECT
            a,
            min(id) AS min_id
        FROM
            b
        GROUP BY
            a
    ) t1 ON t.id = t1.min_id
    WHERE
        t1.min_id IS NULL;
```