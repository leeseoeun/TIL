**SQL Join**<br>
**1. LEFT *OUTER* JOIN** ⭐⭐<br>
*1-1. SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.aid*
- topic 테이블을 왼쪽에 놓고 author 테이블을 오른쪽에 놓음<br>
- topic 테이블의 author_id와 author 테이블의 aid의 값이 같음<br>
- 참고해서 두개의 테이블을 하나로 만듦<br>
```sql
MariaDB [sqldb]> select * from topic left join author on topic.author_id = author.aid;
+-----+------------+------------------+-----------+------+---------+-------+------------+
| tid | title      | description      | author_id | aid  | name    | city  | profile_id |
+-----+------------+------------------+-----------+------+---------+-------+------------+
|   1 | HTML       | HTML is ...      | 1         |    1 | egoing  | seoul |          1 |
|   2 | CSS        | CSS is ...       | 2         |    2 | leezche | jeju  |          2 |
|   3 | JavaScript | JavaScript is .. | 1         |    1 | egoing  | seoul |          1 |
|   4 | Database   | Database is ...  | NULL      | NULL | NULL    | NULL  |       NULL |
+-----+------------+------------------+-----------+------+---------+-------+------------+
```
<br>

*1-2. SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.aid LEFT JOIN profile ON author.profile_id = profile.pid*
```sql
MariaDB [sqldb]> select * from topic left join author on topic.author_id = author.aid left join profile on author.profile_id = profile.pid;
+-----+------------+------------------+-----------+------+---------+-------+------------+------+-----------+------------------+
| tid | title      | description      | author_id | aid  | name    | city  | profile_id | pid  | title     | description      |
+-----+------------+------------------+-----------+------+---------+-------+------------+------+-----------+------------------+
|   1 | HTML       | HTML is ...      | 1         |    1 | egoing  | seoul |          1 |    1 | developer | developer is ... |
|   2 | CSS        | CSS is ...       | 2         |    2 | leezche | jeju  |          2 |    2 | designer  | designer is ..   |
|   3 | JavaScript | JavaScript is .. | 1         |    1 | egoing  | seoul |          1 |    1 | developer | developer is ... |
|   4 | Database   | Database is ...  | NULL      | NULL | NULL    | NULL  |       NULL | NULL | NULL      | NULL             |
+-----+------------+------------------+-----------+------+---------+-------+------------+------+-----------+------------------+
```
<br>

*1-3. SELECT tid, topic.title, author_id, name, profile.title AS job_title FROM topic LEFT JOIN author ON topic.author_id = author.aid LEFT JOIN profile ON author.profile_id = profile.pid*
- topic 테이블에 title이 있고 profile 테이블에도 title이 있기 때문에 *테이블이름.title*<br>
- profile.title에 이름/별명을 붙여 주고 싶으면 *profile.title as 이름/별명*
```sql
MariaDB [sqldb]> select tid, topic.title, author_id, name, profile.title as job_title from topic left join author on topic.author_id = author.aid left join profile on author.profile_id = profile.pid;
+-----+------------+-----------+---------+-----------+
| tid | title      | author_id | name    | job_title |
+-----+------------+-----------+---------+-----------+
|   1 | HTML       | 1         | egoing  | developer |
|   2 | CSS        | 2         | leezche | designer  |
|   3 | JavaScript | 1         | egoing  | developer |
|   4 | Database   | NULL      | NULL    | NULL      |
+-----+------------+-----------+---------+-----------+
```
<br>

*1-4. SELECT tid, topic.title, author_id, name, profile.title AS job_title FROM topic LEFT JOIN author ON topic.author_id = author.aid LEFT JOIN profile ON author.profile_id = profile.pid WHERE aid = 1*
- aid가 1인 것만을 보고 싶으면 *where aid = 1*
```sql
MariaDB [sqldb]> select tid, topic.title, author_id, name, profile.title as job_title from topic left join author on topic.author_id = author.aid left join profile on author.profile_id = profile.pid where aid = 1;
+-----+------------+-----------+--------+-----------+
| tid | title      | author_id | name   | job_title |
+-----+------------+-----------+--------+-----------+
|   1 | HTML       | 1         | egoing | developer |
|   3 | JavaScript | 1         | egoing | developer |
+-----+------------+-----------+--------+-----------+
```
<br>

*1-5. RIGHT OUTER JOIN은 기준이 오른쪽에 있는 테이블*

<br>

[*생활코딩*](https://youtube.com/playlist?list=PLuHgQVnccGMAG1O1BRZCT3wkD_aPmPylq)
