**SQL Join**<br>
**4. EXCULUSIVE JOIN**<br>
- 한개의 테이블에만 존재하는 값으로 테이블을 만듦

*4-1. SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.aid WHERE author.aid is NULL*
```sql
MariaDB [sqldb]> select * from topic left join author on topic.author_id = author.aid where author.aid is null;
+-----+----------+-----------------+-----------+------+------+------+------------+
| tid | title    | description     | author_id | aid  | name | city | profile_id |
+-----+----------+-----------------+-----------+------+------+------+------------+
|   4 | Database | Database is ... | NULL      | NULL | NULL | NULL |       NULL |
+-----+----------+-----------------+-----------+------+------+------+------------+
```

<br>

[*생활코딩*](https://youtube.com/playlist?list=PLuHgQVnccGMAG1O1BRZCT3wkD_aPmPylq)
