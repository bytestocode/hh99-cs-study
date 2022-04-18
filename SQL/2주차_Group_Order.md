## GROUP BY, ORDER BY

### GROUP BY
1) 동일한 데이터를 가지는 컬럼 그룹화 하기   
2) 그룹화한 데이터가 표현할 데이터 설정
```sql
그룹화한 컬럼 데이터의 개수
> select name, count(*) from users
> group by name;

그룹화한 컬럼 데이터가 가지는 최솟값인 데이터
> select day, min(commits) from github
> group by day;

그룹화한 컬럼 데이터가 가지는 최댓값인 데이터
> select day, max(commits) from github
> group by day;

그룹화한 컬럼 데이터가 가지는 특정 데이터들의 평균값
> select day, avg(commits) from github
> group by day;

그룹화한 컬럼 데이터가 가지는 특정 데이터들의 합계
> select day, sum(commits) from github
> group by day;
```

### ORDER BY
```sql
group by로 찾은 데이터 정렬 (오름차순)
> select name, count(*) from users
> group by name
> order by count(*);

(내림차순)
> order by count(*) desc;

> select * from github
> order by commits desc;
```

### WHERE과 함께 사용
```sql
> select commits, count(*) from github
> where day = "월요일"
> group by commits;    
```

### Alias
```sql
> select commits, count(*) as cnt from github g
> where g.day = '월요일'
> group by commits
```

### 숙제
```sql
> select 결제수단, count(*) from 주문테이블
> where 이메일 like '%@naver.com' and 강의명 = '앱개발 종합반'
> group by 결제수단
```