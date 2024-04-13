<b>1. sql 명령문 개괄</b><br>

1. 순서 정렬 문제 ☆<br>
from - where - group by - having - select - order by

<br>

2. 종류 문제 ☆<br>
    |||
    |-|-|
    |<b>ddl</b>|create, alter, modify, drop, truncate|
    |<b>dml</b>|insert, update, delete, select|
    |<b>dcl</b>|grant, revoke|
    |<b>tcl</b>|commit, rollback|

<br>

<b>2. select</b><br>

1. distinct : 집약<br>
    ||||
    |-|-|-|
    |10||10|
    |10|=>|20|
    |20||30|
    |20|||
    |20|||
    |30|||

    ```sql
    [예] distinct deptno, mrg (= distinct(deptno, mgr))
    => deptno, mgr에 대해서 distinct
    ```

<br>

2. as (alias)<br>
    1. select절<br>
        1. as 생략 가능<br>
        2. 칼럼 이름에 띄어쓰기가 있는 경우 " [예] "부서 번호"]
        
        <br>

    2. from절<br>
        1. as 사용 불가능!
        
        <br>

    3. concat<br>
        |||
        |-|-|
        |<b>+</b>|sql server|
        |<b>\|\|</b>|오라클|
        |<b>concat()|인수가 무조건 2개 (3개, 4개 불가능)|

<br>

<b>3. 논리 연산자</b><br>

1. <br>
    
    ||||
    |-|-|-|
    |<b>and</b>|a and b|a와 b 둘 다|
    |<b>or</b>|a or b|a 또는 b 둘 중 하나|
    |<b>not</b>|not a, b|a와 b 둘 다 x|

<br>

2. 연산 순위 ☆<br>
not -> and -> or<br>

```sql
[예] not <조건> and <조건> and not <조건> or <조건>
-> not에의해서바뀐조건 and <조건> and not에의해서바뀐조건 or <조건>
=> and에의해서바뀐조건 or <조건>
```

<br>

<b>4. sql 연산자</b><br>

1. <br>

    ||||
    |-|-|-|
    |<b>between and</b>|a between 1 and 2|a가 1 이상 2 이하|
    |<b>in</b>|in(1, 2, 3)|a = 1 또는 a = 2 또는 a = 3|
    |<b>like ☆|_|미지의 한글자|
    ||%|0 이상의 한 글자|

    ```sql
    [예] _l% => 두번째 글자가 l로 시작


    escape : 와일드 카드(_, %)를 문자로 취급하는 함수
    
    [예] ename like 'a_a'
    => 'a@_a' escape '@' (아무 문자나 됨)
    ```

<br>

2. rownum, top ☆<br>
    1. rownum<br>
        1. 오라클<br>
        2. where 조건 절에서 rownum이 1인 경우 포함<br>

    ```sql
    [예]
    select empno, sal
    from enpm
    where rownum <= 3
    order by sal desc -> 가장 마지막에 실행
    => sal 정렬 전 rownum의 값을 가지고 온 후, order by 실행
    ```

    <br>

    2. top<br>
        1. sql server<br>
        2. select절<br>

    ```sql
    [예]
    select top(n) <컬럼명>
    => 상위 n개의 <컬럼명>을 가지고 옴
    ```

<br>

<b>5. null ☆☆☆</b><br>

1. null의 정의 : 부재, 모르는 값

<br>

2. 산술 연산, 비교 연산<br>
`산술 연산`에서 null + 2, null - 4, null x null => null로 나옴 (알 수 없음(unknown))
<br><br>
`비교 연산`에서 null = 2, null = null이 되면<br><br>
-> where(조건)<br>
-> where(unknown)<br>
=> false가 됨

<br>

3. 정렬상 의미<br>
    |||오름차순 기준|
    |-|-|-|
    |오라클|무한대|맨 마지막으로 나옴
    |sql server|-무한대|맨 처음으로 나옴

<br>

4. ☆<br>

|||||
|-|-|-|-|
|<b>nvl</b>|널뛰기|nvl(값1, 값2)|값1 is null -> 값2|
|<b>nvl2</b>|널뛰기|nvl2(값1, 값2, 값3)|값1 is null -> <b>값3</b>|
|<b>is null</b>|널뛰기|is null(값1, 값2)|값1 is null -> 값2|
|<b>null if</b>|같이 널자|null if(값1, 값2)|값1 = 값2 -> null / 다르면 값1|
|<b>coalesce</b>|널 아닌 첫번째 값|coalesce(값1, 값2, ...)|널 아닌 첫번째 값|

<br>

<b>6. 정렬 (order by)</b><br>

1. 특성<br>
    1. 가장 마지막에 실행<br>
    2. 정렬 때문에 성능이 느려질 수 있음<br>
    3. null값과의 관계 ((-)무한대)

<br>

2. 칼럼 번호 정렬<br>
    1. 출력되는 칼럼의 수보다 큰 값 불허 (오류)<br>
    2. 출력되지 않는 칼럼 이름으로 정렬 가능<br>

    ```sql
    [예]
    select ename
    order by sal
    ```

<br>

3. 인수 두개 정렬<br>

```sql
[예]
order by sal desc, ename asc
=> sal이 값으면 ename 오름차순으로 정렬
```

<br>


<b>7. 숫자 함수</b><br>

||||
|-|-|-|
|<b>round</b>|자릿수 확인|round(136.93, <b>인수!</b>)|
|<b>ceil</b>|오라클||
|<b>ceiling</b>|sql server||

<br>

<b>8. 문자 함수</b><br>

||||
|-|-|-|
|<b>upper</b>|<b>lower</b>||
|<b>lpad</b>|<b>rpad</b>|문자 채우기|
|<b>ltrim</b>|<b>rtrim</b>||
|<b>substr</b>|||
|<b>instr</b>||문자 찾기|
|<b>to_char</b>|<b>to_date</b>|[문제 예] 다음 중 데이터의 형 변환을 일으키는 함수는?|
|<b>sysdate</b>||오라클|
|<b>getdate</b>||sql server|

<br>

[문제 예] 날짜 데이터 + 숫자 => 숫자일 이후 (숫자를 day로 인식)

<br>

<b>9. decode/case</b><br>

```sql
case
when then 조건 1
when then 조건 2
else // else x, 조건 1, 2 만족 x => null 출력
end
```

<br>

<b>10. 집계함수 ☆☆☆</b><br>

1. null과의 관계<br>
    [예]<br>
    |a|b|c||sum(a + b + c)|
    |-|-|-|-|-|
    |null|null|1||null|
    |2|3|2||7|
    |2|null|3||null|

    ```sql
    sum(a) = 4      // null 제외
    sum(b) = 3      // null 제외
    => null을 건너뛰고 계산

    sum(a + b + c) = 7
    sum(a) + sum(b) + sum(c) = 13
    => 둘의 차이 잘 알기

    count(a) = 2    // null 제외
    count(*) = 3
    ```

<br>

<b>11. group by</b><br>

1. 집약 기능<br>
2. 정보를 그룹으로 바꿈

<br>

<b>12. join</b><br>

1. natural join / using<br>
    1. 중복된 컬럼 한개만 출력<br>
    2. 중복된 컬럼 가장 앞에 출력<br>
    3.  alias 사용 불가능
    
<br>

2. left outer join<br>
```sql
a left outer join b
on a.col1 = b.col1

= where a.col1 = b.col1(+)

=> (+) 위치 잘 알기(left는 오른쪽 테이블에 (+)를 붙임)
```

<br>

3. 조인을 하면 할수록 칼럼이 계속 늘어나서 테이블이 뚱뚱해짐

<br>

4. 조인 순서<br>
```sql
from a, b, c
=> from a,b로조인한결과, c
```

<br>

<b>13. 서브쿼리</b><br>

1. <br>
|||
|-|-|
|<b>select</b>|<b>scalar</b> 서브 쿼리|
|<b>from</b>|<b>inline view</b> 서브 쿼리 (메인 쿼리의 칼럼 사용 가능)|
|<b>where</b>|<b>nested</b> 서브 쿼리 (거의 모든 서브 쿼리)|
|<b>group by</b>|서브 쿼리 불가능|
|<b>having</b>|<b>nested</b> 서브 쿼리 (거의 모든 서브 쿼리)|
|<b>order by</b>|<b>scalar</b> 서브 쿼리|

<br>

2. <br>
```sql
select
from a
where ( select
        from b
        where a.col1 ... )

=> a 테이블의 행 하나를 읽을 때마다 서브 쿼리 전체를 다 돌림
(서브쿼리에 한해서 a.col 값이 고정되어 있음)
```

<br>

3. in, any/some, all, exist 의미 기억하기<br>

|exist|'a', '1' 등을 다 출력할 수 있음|
|-|-|
|true|출력할 게 있음|
|flase|출력할 게 없음|

<br>

<b>14. 집합 연산자</b><br>

|||
|-|-|
|<b>union</b><br><b>intersect</b><br><b>minus</b> <i>(오라클)</i><br><b>except</b> <i>(sql server)</i>|정렬 작업 o, 느림|
|<b>union all</b>|정렬 작업 x, 빠름, 중복 데이터 존재|

<br>

<b>15. ddl</b><br>

||||
|-|-|-|
|<b>drop</b>|건물 철거<br>(구조 삭제)||
|<b>truncate</b>|입주민 퇴거<br>(구조가 남음)|auto commit<br>rollback 불가능|
|<b>delete</b>||유저 commit<br>rollback 가능|

<br>

<b>16. dml</b><br>

1. <br>
|||
|-|-|
|<b>insert</b>|insert values 시 개수가 다른 경우 오류|
|<b>update</b>|
|<b>delete</b>|
|||
|<b>merge</b>|<i>기출 37회 참고<i>|

<br>

2. tcl<br>
    1. 유저 commit
    2. rollback 가능

<br>

<b>17. 제약 조건 ☆</b><br>

|||
|-|-|
|<b>pk</b>|unique + not null, 한개만 존재 (대표성)|
|<b>unique</b>||
|<b>not null</b>||

<br>

<b>18. dcl</b><br>

1. grant, revoke<br>
```sql
grant 권한 on 테이블 to 유저
revoke 권한 on 테이블 from 유저

[문제 예] 정의를 주고 단어를 물어봄
[문제 예] 문법을 물어봄
```

<br>

2. role 특징<br>
    1. role : 권한의 집합<br>
    2. 사람에게 부여할 수 있음<br>
    3. 같은 role을 가질 수 있음<br>
    4. role 부여 시 권한이 필요함<br>
    5. 명령어가 아닌, 객체 (object)의 하나<br>

<br>

<b>19. view</b><br>

|view|독편부|
|-|-|
|<b>독</b>립성|기존 테이블의 구조가 변경되면 뷰도 변경됨,<br>업데이트 할 필요 없음|
|<b>편</b>리성|테이블을 조작할 필요 없음|
|<b>보</b>안성|원하는 정보만 보여 주고 나머지는 숨겨서 보여 줄 수 있음|

<br>

<b>20. 그룹 함수 ☆☆☆</b><br>

|||
|-|-|
|<b>rollup</b>|rollup(a, b) `!=` rollup(b, a)|
|<b>cube</b>|cube(a, b) `=` cube(b, a)|
|<b>grouping sets</b>||
||
|<b>grouping</b>||

<br>

[문제 예] 결과 값을 주고 어떤 함수를 썼는지 물어봄<br>
1. null 찾기<br>
2. 총합 행 있는지 찾기<br>
    1. 있음
        1. 한쪽에 결과가 있음, 행의 개수가 적음 => `rollup`<br>
        2. 양쪽에 결과가 있음, 행의 개수가 많음 => `cube`<br>
    2. 없음 => `grouping sets`<br>

<br>

<b>21. tcl</b><br>

1. commit<br>
2. rollback<br>
3. auto commit off and begin transaction<br>
