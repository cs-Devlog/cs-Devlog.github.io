---
title: Oracle ANSI SQL과 INNER/OUTER JOIN 차이
date: 2019-05-17- 23:00:00
description: Oracle ANSI SQL과 INNER/OUTER JOIN 차이에 대해 알아보자.
categories:
- Database
tags: 
- Database
- ANSI SQL
- INNER JOIN
- OUTER JOIN
---
# < ANSI SQL >
ANSI SQL에 대해 알아보자.
1. 표준 SQL문이기 때문에 DBMS의 종류에 제약을 받지 않는다. (MySQL, OracleDB..)
2. 테이블간의 Join 관계가 FROM 에서 명시되기 때문에 WHERE 문에서 조건만 확인하면 된다.

즉, 가독성이 일반 Query문보다 좋다.

대표적인 예시로 ANSI SQL의 두번째 장점인 가독성에 대해서알아보자.

일반 SQL Query는 다음과 같다.

~~~SQL
-- 일반적인 SQL Query
SELECT * 
FROM table1 as t1, table2 as t2 WHERE t1.a = t2.b
~~~

즉, WHERE문에서 Table을 JOIN하는 방식이다.

단순한 Query라면 가독성에 전혀 문제가 없지만, Query가 길어지게되면 가독성이 떨어질 수 밖에 없다.

이와 다르게 ANSI SQL Query 는 FROM 절에서 JOIN을 이용하여 묶고, WHERE에는 검색 조건만 넣어 가독성이 좋다.

~~~SQL
-- ANSI SQL Query 
SELECT * 
FROM table1 as t1 LEFT OUTER JOIN table as t2 ON t1.a = t2.b
~~~

위의 ANSI SQL에서는 LEFT OUTER JOIN을 사용하여 FROM절에 Table JOIN 하였다.

ANSI SQL에서 사용하는 INNER/OUERT JOIN 의 개념을 명확히 아는 것 또한 중요하다.

***

# < INNER JOIN >
두 테이블간 ON 조건을 만족하는 ROW만 출력된다.

~~~SQL
-- INNER JOIN 
SELECT * 
FROM table1 as t1 INNER JOIN table2 as t2 ON t1.a = t2.b;
~~~

Query가 위와 같을 때, ON 조건인 t1.a = t2.b 를 만족하는 Row 만 출력된다.

# < OUTER JOIN >
대표적으로 자주 사용하는 LEFT OUTER JOIN 에 대해서 알아보자.

OUTER 명령어는 생략이 가능하다. 즉, LEFT OUTER JOIN = LEFT JOIN과 같다.

LEFT TABLE 을 기준으로 오른쪽에 덧붙이는 느낌으로 생각하면 된다.

즉, LEFT TABLE의 결과값을 가져오고 ON 조건에 해당하는 경우 오른쪽에 매칭, 데이터가 없는 경우 NULL로 출력된다.

~~~SQL
-- OUTER JOIN 
SELECT * 
FROM table1 as t1 LEFT OUTER JOIN table2 as t2 ON t1.a = t2.b;
~~~

t1.a = t2.b 인 경우, t1의 값이 10행 이라면, 해당 쿼리의 결과도 10행이 유지되고, ON 조건에 해당하는 Row가 있다면 오른쪽에 데이터가 매칭된다.

단, 1개의 t1 행에 ON 조건을 만족하는 t2의 값이 여러개라면, Row가 증가할 수도 있다.

***

# < 결론 >
ANSI SQL 에 맞춰서 Query를 짜는 습관을 가지자.

즉, WHERE 문에서는 검색조건만 넣도록, Table JOIN 은 FROM절에 묶어서 처리하자.