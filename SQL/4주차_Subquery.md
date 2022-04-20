## Subquery

### 쿼리 안의 쿼리
#### where 관련
```sql
select u.user_id, u.name, u.email from users u
where u.user_id in (
  select user_id from orders
  where payment_method = 'kakaopay'
)

1. <sub-from> 주문 목록 테이블에서
2. <sub-where> 결제 수단이 '카카오 페이'인 경우
3. <sub-select> user_id를 조회

4. <from> 유저 테이블에서
5. <where> user_id가 subquery의 결과에 포함되는 경우
6. <select> user_id, name, email을 조회
```
#### select 관련
```sql
select c.checkin_id, c.user_id, c.likes, 
	(select avg(likes) from checkins c2
	where c2.user_id = c.user_id) as avg_like_user
from checkins c;

1. <from> checkins 테이블에서
2. <select> checkin_id, user_id, likes, avg_like_user(서브쿼리)

3. <sub-from> checkins 테이블에서
4. <sub-where> user_id가 user_id와 같다면??
5. <sub-select> 좋아요수 평균을 조회
```
#### from 관련
```sql
select pu.user_id, a.avg_like, pu.point from point_users pu
inner join (
	select user_id, round(avg(likes),1) as avg_like from checkins
	group by user_id
) a on pu.user_id = a.user_id

1. <sub-from> checkins 테이블에서
2. <sub-group by> user_id를 기준으로 그룹화
3. <sub-select> user_id와 소수점 1자리까지 구한 좋아요 평균을 조회

4. <from> 포인트 유저 테이블에서
5. <join> 포인트 유저 테이블의 user_id와 서브쿼리의 user_id를 기준으로 join
6. <select> user_id, 서브쿼리의 avg_like, point 조회
```

#### with 절 ??
```sql
with table1 as (
	select course_id, count(distinct(user_id)) as cnt_checkins from checkins
	group by course_id
), table2 as (
	select course_id, count(*) as cnt_total from orders
	group by course_id
)

select c.title,
       a.cnt_checkins,
       b.cnt_total,
       (a.cnt_checkins/b.cnt_total) as ratio
from table1 a inner join table2 b on a.course_id = b.course_id
inner join courses c on a.course_id = c.course_id
```

#### string 관련
```sql
select user_id, email, SUBSTRING_INDEX(email, '@', 1) from users
@를 기준으로 나누고, 첫번째 부분을 가져옴
```
```sql
select user_id, email, SUBSTRING_INDEX(email, '@', -1) from users
@를 기준으로 나누고, 마지막 부분을 가져옴
```
```sql
select order_no, created_at, substring(created_at,1,10) as date from orders
substring의 첫번째 인자에 해당하는 컬럼에서 두번째~세번째 인자 까지의 문자열을 반환
```
#### case
```sql
select pu.point_user_id, pu.point,
case 
when pu.point > 10000 then 'Good!'
else 'Bad!'
END as '구분'
from point_users pu;

1. <from> 포인트 유저 테이블에서
2. <select> user_id, point, case 컬럼 조회
3. <case> point가 10000 초과이면 'Good!' 이하면 'Bad!' 값을 가지는 컬럼 
```
