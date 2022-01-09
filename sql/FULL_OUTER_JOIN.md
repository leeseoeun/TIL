**SQL Join**<br>
**3. FULL OUTER JOIN**<br>
- 모든 테이블의 모든 값으로 테이블을 만듦
- left *outer* join과 right *outer* join을 합쳐서(union distinct) 중복되는 것을 제거한 것

*3-1. SELECT * FROM topic FULL OUTER JOIN author ON topic.author_id = author.id<br>
(SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id) UNION (SELECT * FROM topic RIGHT JOIN author ON topic.author_id = author.id)*
```sql
MariaDB [sqldb]> select * from topic left join author on topic.author_id = author.aid union select * from topic right join author on topic.author_id = author.aid;
+------+------------+------------------+-----------+------+----------+--------+------------+
| tid  | title      | description      | author_id | aid  | name     | city   | profile_id |
+------+------------+------------------+-----------+------+----------+--------+------------+
|    1 | HTML       | HTML is ...      | 1         |    1 | egoing   | seoul  |          1 |
|    2 | CSS        | CSS is ...       | 2         |    2 | leezche  | jeju   |          2 |
|    3 | JavaScript | JavaScript is .. | 1         |    1 | egoing   | seoul  |          1 |
|    4 | Database   | Database is ...  | NULL      | NULL | NULL     | NULL   |       NULL |
| NULL | NULL       | NULL             | NULL      |    3 | blackdew | namhae |          3 |
+------+------------+------------------+-----------+------+----------+--------+------------+
```

[*생활코딩*](https://youtube.com/playlist?list=PLuHgQVnccGMAG1O1BRZCT3wkD_aPmPylq)
