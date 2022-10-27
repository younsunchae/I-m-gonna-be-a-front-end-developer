### 🍀 order by
우선순위가 있는 열을 순서대로 적기
<br/>

### 🍀 like : 부분 일치
1. 'a%' : a로 시작되는 모든 것
2. 'a_%_%' : a로 시작되고 최소 3자 이상
3. '_a%' : 두번째ㅔ 자리에 a가 들어가는 것
4. '%a%' : 중간에 a이 들어가는 것
5. not like : 부분 일치 하지 않은 것
<br/>

### 🍀 limit : 제한
```sql
order by name limit 2
```
name 오른차순으로 정렬한 후 2개
<br/>

### 🍀distinct : 중복 제거
```sql
select count(distinct name)...
```
중복제거한 name count
<br/>

### 🍀 ifnull : null값 찾기
```sql
select ifnull(name, "NONE") as name
```
name 값이 null 이면 NONE, 아니면 name 값
<br/>

### 🍀 date_format : date 칼럼 지정한 형식으로 출력
```sql
select data_format(data_time, '%Y-%m-%d')...
```
data_time을 Y-m-d 형식으로 출력<br/>
%s(초), %t(hh:mm:SS) 대소문자 별로 출력 형식 다름
<br/>

### 🍀 group by 
```sql
 group by user_id, product_id having count(*) >=2 
 ```
 user_id와 product_id가 2개 이상인 행 찾기
 <br/>

 ### 🍀 join

 #### inner join : 교집합
 ```sql
 select test1.number from test1 join test2 on test1.number = test2.number; 
```
```sql
select distinct c.cart_id from cart_products c inner join cart_products p on(c.cart_id = p.cart_id) where (c.name ='우유' and p.name='요거트') or (c.name='요거트' and p.name='우유') order by c.cart_id;
```
<br/>

#### outer join : 매칭되는 값이 없어도 출력
```sql
select test1.*, test2.number from test1 left outer join test2 on test1.number = test2.number;
```

### 🍀 union
중복값 제거하면서 테이블 합치고 싶을 때
```sql
select * from customers union select city from orders order by city
```


#### union all
중복값 안 제거 하고 싶을 때
<br/>

### 🍀 case
```sql
select seq
    case
        when (조건) then 결과
            case 
        when(조건) then 결과
        else 결과
        end as case_result
    from 'user' u
```
else 생략 하면 클남