---
title:  "[SQL DB] 데이터 분석 단계로 나아가기"
excerpt: "step 04"

categories:
  - SQL DB

toc: true
toc_sticky: true
toc_label: "데이터 분석 단계로 나아가기"

last_modified_at: 2021-11-10
---

## 1. 데이터의 특성 구하기

특정 컬럼의 값을 가진 로우 수를 구하고 싶다면 아래와 같이 작성하면 된다.<br>
이 때 해당 컬럼의 값이 NULL이면 그 로우는 카운트하지 않는다.
```sql
SELECT COUNT(col) FROM dbname.tablename;
```

컬럼의 값이 NULL인 로우는 카운트하지 않기 때문에,<br>
전체 로우의 수를 알고 싶을 때는 불편할 수도 있다.<br>
따라서, 그런 경우에는 아래와 같이 SQL문을 작성하면 된다.
```sql
SELECT COUNT(*) FROM dbname.tablename;
```

특정 컬럼에서 가장 큰 값 또는 가장 작은 값을 찾고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT MAX(col) FROM dbname.tablename;
SELECT MIN(col) FROM dbname.tablename;
```

특정 컬럼의 평균을 구하고 싶다면 아래와 같이 작성하면 된다.<br>
AVG 함수도 계산할 때 NULL을 포함하지 않으므로 NULL이 포함돼서 이상한 값이 나올 일은 없다.
```sql
SELECT AVG(col) FROM dbname.tablename;
```

특정 컬럼의 합을 구하고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT SUM(col) FROM dbname.tablename;
```

특정 컬럼의 표준편차를 구하고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT STD(col) FROM dbname.tablename;
```

이러한 집계함수들 외에도 각 로우마다 단순한 산술 연산을 해주는 산술 함수들도 있다.<br>
산술 함수에는 아래와 같은 함수들이 있다.
```sql
SELECT ABS(col) FROM dbname.tablename;      # 절댓값을 구하는 함수
SELECT SQRT(col) FROM dbname.tablename;     # 제곱근을 구하는 함수
SELECT CEIL(col) FROM dbname.tablename;     # 올림 함수
SELECT FLOOR(col) FROM dbname.tablename;    # 내림 함수
SELECT ROUND(col) FROM dbname.tablename;    # 반올림 함수
```
이 외에도 다양한 산술 함수들이 있는데, 다른 것들이 궁금하다면 [여기](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html)를 참고하자.