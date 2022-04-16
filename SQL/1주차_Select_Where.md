## SELECT, WHERE

```sql
> SQL
> sequelize
```

### SHOW
테이블 불러오기
```sql
> SHOW TABLES;
```

### SELECT
컬럼 불러오기
```sql
> SELECT * FROM [테이블명];
> [테이블명].findAll({});

> SELECT [컬럼명] [컬럼명] FROM [테이블명];
> 테이블명.findAll({
    attributes: ['컬럼명', '컬럼명'],
  });
```

### WHERE
조건을 만족하는 컬럼 불러오기
```sql
> SELECT * FROM [테이블명]   
> WHERE [컬럼명] = "조건";
> where: { 컬럼명: "조건" }
    
> WHERE [컬럼명1] = "조건1" and [컬럼명2] = "조건2";
> where: { 컬럼명1: "조건1", 컬럼명2: "조건2" }

> WHERE [컬럼명] > 20000;
> where: { 컬럼명: { [Op.gt]: 20000 }};
 
> WHERE [컬럼명] = "황**";
> where: { 컬럼명: { [Op.regexp]: "황.." }}

> WHERE [컬럼명] != "조건";
> where: { 컬럼명: { [Op.ne]: "조건" } }

> WHERE [컬럼명] BETWEEN "2020-07-13" AND "2020-07-15";
> where: { 컬럼명: { [Op.between]: ["2020-07-13", "2020-07-15"] } }

> WHERE [컬럼명] IN (1, 3);
> where: { 컬럼명: { [Op.in]: [1, 3] }}

> WHERE [컬럼명] LIKE "%gmail.com";
> where: { 컬럼명: { [Op.like]: "%gmail.com" }}
```

### LIMIT
가져올 데이터 로우 개수 제한
```sql
> SELECT * FROM [테이블명]
> WHERE [컬럼명] = "조건"
> LIMIT 5;

> 테이블명.findAll({ where: { 컬럼명: "조건" }, limit: 5 });
```

### DISTINCT
```sql
> SELECT DISTINCT([컬럼명]) FROM [테이블명];
> 테이블명.findAll({ attributes: '컬럼명', distinct: true });
```

### COUNT
```sql
> SELECT COUNT(*) FROM [테이블명];
> 테이블명.count();

> SELECT COUNT(DISTINCT([컬럼명])) FROM [테이블명];
> 테이블명.count({ distinct: true, col: "컬럼명" });
```
