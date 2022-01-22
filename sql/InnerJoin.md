**SQL Join**<br>
**2. *INNER* JOIN** ⭐<br>
- left, right, outer가 없으면 *inner* join
- 모든 테이블에 존재하는 값으로 테이블을 만듦 (null 값이 존재하지 않음)

*2-1. SELECT * FROM topic INNER JOIN author ON topic.author_id = author.aid*
```sql
MariaDB [sqldb]> select * from topic inner join author on topic.author_id = author.aid;
+-----+------------+------------------+-----------+-----+---------+-------+------------+
| tid | title      | description      | author_id | aid | name    | city  | profile_id |
+-----+------------+------------------+-----------+-----+---------+-------+------------+
|   1 | HTML       | HTML is ...      | 1         |   1 | egoing  | seoul |          1 |
|   2 | CSS        | CSS is ...       | 2         |   2 | leezche | jeju  |          2 |
|   3 | JavaScript | JavaScript is .. | 1         |   1 | egoing  | seoul |          1 |
+-----+------------+------------------+-----------+-----+---------+-------+------------+

MariaDB [sqldb]> select * from topic join author on topic.author_id = author.aid;
+-----+------------+------------------+-----------+-----+---------+-------+------------+
| tid | title      | description      | author_id | aid | name    | city  | profile_id |
+-----+------------+------------------+-----------+-----+---------+-------+------------+
|   1 | HTML       | HTML is ...      | 1         |   1 | egoing  | seoul |          1 |
|   2 | CSS        | CSS is ...       | 2         |   2 | leezche | jeju  |          2 |
|   3 | JavaScript | JavaScript is .. | 1         |   1 | egoing  | seoul |          1 |
+-----+------------+------------------+-----------+-----+---------+-------+------------+
```
<br>

*2-2. SELECT * FROM topic INNER JOIN author ON topic.author_id = author.id INNER JOIN profile ON profile.pid = author.profile_id*
```sql
MariaDB [sqldb]> select * from topic join author on topic.author_id = author.aid join profile on profile.pid = author.profile_id;
+-----+------------+------------------+-----------+-----+---------+-------+------------+-----+-----------+------------------+
| tid | title      | description      | author_id | aid | name    | city  | profile_id | pid | title     | description      |
+-----+------------+------------------+-----------+-----+---------+-------+------------+-----+-----------+------------------+
|   1 | HTML       | HTML is ...      | 1         |   1 | egoing  | seoul |          1 |   1 | developer | developer is ... |
|   3 | JavaScript | JavaScript is .. | 1         |   1 | egoing  | seoul |          1 |   1 | developer | developer is ... |
|   2 | CSS        | CSS is ...       | 2         |   2 | leezche | jeju  |          2 |   2 | designer  | designer is ..   |
+-----+------------+------------------+-----------+-----+---------+-------+------------+-----+-----------+------------------+
```

<br>

[*생활코딩*](https://youtube.com/playlist?list=PLuHgQVnccGMAG1O1BRZCT3wkD_aPmPylq)
