---
title:  "[SQL DB] 데이터 조회로 기본 다지기"
excerpt: "데이터 조회로 기본 다지기"

categories:
  - SQL DB

toc: true
toc_sticky: true
toc_label: "데이터 조회로 기본 다지기"

last_modified_at: 2021-10-30
---

## 1. SELECT와 WHERE

이번에는 테이블 안에서 데이터를 찾아보자.

먼저, 아래의 쿼리문을 분석해보자.

```sql
SELECT * FROM dbname.tablename;
```
위의 쿼리문을 실행하면 아래와 같은 화면이 나온다.

<img src = "/assets/images/SQL DB/select_all_query.png" width = "80%" height = "80%">

하나하나 뜯어서 보면,
```sql
SELECT: 테이블의 데이터를 조회할 때 사용하는 구문
*: 공식 명칭은 asterisk, 각 row의 모든 column들을 보여달라는 뜻
FROM dbname.tablename: 해당 데이터베이스에서 해당 테이블로부터 데이터를 가져온다는 뜻
```

이번에는 각 row의 모든 column 말고 특정 column을 지정해서 가져오려면 아래와 같이 쿼리문을 구성하면 된다.
```sql
SELECT column1, column2, ... FROM dbname.tablename;
```

나는 email, age, address column을 가져와보겠다.<br>
결과는 아래와 같다.

<img src = "/assets/images/SQL DB/select_column_query.png" width = "50%" height = "50%">

여기까지가 column을 선택해서 데이터를 가져오는 방법이었고,<br>
이제 row를 선택해서 데이터를 가져와보자.

```sql
SELECT column1, column2, ... FROM dbname.tablename WHERE column = value;
```

```sql
WHERE: 특정 조건을 만족하는 row들만 조회하려고 할 때 사용
```

## 2. SQL 작성 형식

1. SQL문 끝에는 항상 세미콜론을 써줘야 한다.
2. SQL문 안에는 공백이나 개행 등을 자유롭게 넣을 수 있다.<br>
그러니까, 아래처럼 SQL문을 작성할 수 있다는 말이다.<br>
이런 성질을 이용해서 유연하게 가독성을 높이는 것이 좋은 방법이다.
```sql
SELECT *           FROM ~~
    WHERE ~~~; #adsf
```
3. SQL문을 작성할 때에, MySQL에 기본적으로 내장된 키워드들(예약어 라고 한다.)은 대문자로 써주는 것이 관례이다.
4. 앞에서는 어떤 테이블을 특정하기 위해서 dbname.tablename방식의 SQL문을 사용했는데,<br>
항상 그렇게 할 필요는 없고 아래와 같이 사용할 수도 있다.<br>
서로 다른 DB에 같은 이름의 table이 존재할 수 있기 때문에 앞서 보인 것처럼 쓰는게 좋은 방법이니 상황에 따라 유연하게 사용하자.
```sql
USE dbname;
SELECT * FROM tablename;
```

## 3. 조건을 나타내는 다양한 방법

- 값을 비교하는 방법<br>
<div class="language-sql highlighter-rouge">
    <div class="highlight">
        <pre class="highlight">
            <code>
                <span class="k">WHERE</span> <span class="n">col</span> <span class="o">=</span> <span class="n">val</span>
            </code>
        </pre>
    </div>
</div>
1. col = val: 값이 같은지 확인
2. col != val: 값이 다른지 확인
3. col >= val: col의 값이 val보다 크거나 같은지 확인, 마찬가지로 >, <=, <도 사용 가능하다.
4. col > '2019-01-01': DATE 타입에 대해서도 부등호 사용이 가능하다. 이 경우에는 col이 2019-01-01 이후인지 확인.
5. col BETWEEN val1 AND val2;
```sql
WHERE col = val;  # 값이 같은지 확인
WHERE col != val;  # 값이 다른지 확인
WHERE col >= val;  # col의 값이 val보다 크거나 같은지 확인, 마찬가지로 >, <=, < 도 사용 가능하다.
WHERE col > '2019-01-01';  # DATE 타입에 대해서도 부등호 사용이 가능하다.
                            # 앞의 경우에는 col이 2019-01-01 이후인지 확인

WHERE col BETWEEN val1 AND val2;  # col의 값이 [val1, val2]에 포함되는지 확인
WHERE col BETWEEN '2019-01-01' AND '2019-12-31';  # DATE 타입에 대해서도 BETWEEN 을 사용할 수 있는데,
                                                    # 앞의 경우에는 col이 2019년 이내인지 확인

WHERE col NOT BETWEEN val1 AND val2;  # col의 값이 [val1, val2]에 포함되지 않는지 확인
```