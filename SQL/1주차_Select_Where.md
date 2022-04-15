## SELECT, WHERE 

### SHOW
테이블 불러오기
```sql
> SHOW TABLES;
```

### SELECT
컬럼 불러오기
```sql
> SELECT * FROM [테이블명];

> SELECT [컬럼명] [컬럼명] FROM [테이블명];
```

### WHERE
조건을 만족하는 컬럼 불러오기
```sql
> SELECT * FROM [테이블명]   
> WHERE [컬럼명] = "조건";
    
> WHERE [컬럼명] = "조건" and [컬럼명] = "조건";

> WHERE [컬럼명] > 20000;
 
> WHERE [컬럼명] = "황**";

> WHERE [컬럼명] != "조건";

> WHERE [컬럼명] BETWEEN "2020-07-13" AND "2020-07-15";

> WHERE [컬럼명] IN (1, 3);

> WHERE [컬럼명] LIKE "%gmail.com";
```

### LIMIT
가져올 데이터 개수 제한
```sql
> SELECT * FROM [테이블명]
> WHERE [컬럼명] = "조건"
> LIMIT 5;
```

### DISTINCT
```sql
> SELECT DISTINCT([컬럼명]) FROM [테이블명];
```

### COUNT
```sql
> SELECT COUNT(*) FROM [테이블명];

> SELECT COUNT(DISTINCT([컬럼명])) FROM [테이블명];
```

