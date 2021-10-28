---
title:  "[SQL DB] 테이블 생성하기"
excerpt: "테이블 생성하기"

categories:
  - SQL DB

toc: true
toc_sticky: true
toc_label: "테이블 생성하기"

last_modified_at: 2021-10-29
---

## 1. CSV 파일로 테이블 생성하기

테이블을 생성하는 방법은 크게 2가지가 있다.<br>
첫 번째는 SQL 문으로 생성하는 방법이고,<br>
두 번째는 CSV 파일을 import 해서 테이블로 만드는 방법이다.

지금은 데이터베이스와 테이블이 이미 존재하고, 그 안에 데이터도 이미 저장된 상황을 가정하고 데이터를 분석하는 것에 집중해서 공부해볼 것이므로 두 번째 방법을 이용해서 테이블을 만들어 볼 것이다.

나는 codeit을 이용해서 공부하고 있으므로 codeit에서 제공하는 CSV 파일을 이용한다.

CSV는 Comma Separated Values의 약자로, 모든 값들이 ,로 구분된 형식의 내용을 가진 파일을 말한다.<br>
컴퓨터에 MS Office가 설치되어 있다면 아마 CSV파일이 Excel로 열리게 되어있을 텐데, CSV 파일의 가장 raw 한 모습을 보고 싶다면 간단한 text editor를 이용해서 열어보는 것이 좋다.

내가 사용한 파일의 내용은 아래와 같다.

<img src = "/assets/images/SQL DB/csv_contents.png" width = "80%" height = "80%">

Workbench에는 CSV파일을 그대로 테이블로 만들어주는 기능이 있는데, 이를 이용해 codeit에서 다운로드한 파일로 member라는 이름의 테이블을 생성해보겠다.

1. 앞서 만든 데이터베이스 이름에 대고 우클릭을 하면 뜨는 팝업에서 Table Data Import Wizard를 클릭
2. CSV 파일을 임포트해서 바로 테이블로 만들 수 있다는 문구가 있는 창이 뜨는데, Browse를 해서 import 하려는 CSV 파일을 선택해주고 Next를 누른다.
3. 선택한 CSV 파일로 생성할 테이블의 이름을 설정하는 창이 뜨면 이름을 member로 정해주고 Next를 누른다.
4. 그 다음 뜨는 창에서 스패너 모양 아이콘을 선택해서 구분자를 , 로 바꿔주고 Next
5. 각 칼럼의 Data Type(또는 Field Type)을 원하는 대로 선택해주고 Next

위와 같은 방식으로 Table을 생성해주면 Table dbname.member was created 라는 문구가 있는 창이 뜨면 성공적으로 dbname 데이터베이스의 member 테이블을 생성한 것이다.

## 2. 생성된 테이블 살펴보기

위에서 테이블을 잘 생성했다면, 생성한 테이블을 살펴볼 필요가 있다.

테이블의 column들을 보고 싶다면 schemas 에서 만든 table의 이름 옆에 마우스를 갖다 대면 세 개의 버튼이 나오는데, 그것 중 가운데 버튼을 누르면 아래와 같이 각 column들을 살펴볼 수 있다.

<img src = "/assets/images/SQL DB/table_overview.png" width = "80%" height = "80%">

## 3. Primary Key 설정하기

<img src = "/assets/images/SQL DB/created_table.png" width = "80%" height = "80%">

위에서 만든 테이블을 살펴보면 이렇게 생겼는데, 여기서 id는 각 row를 고유하게 식별할 수 있도록 하는 column이다. 이것을 Primary Key 라고 한다.<br>
여기서 나는 이 id라는 column을 primary key로 확실히 정해주려고 한다. 그러면 아래 사진처럼 id의 pk에 체크를 해주면 된다.

<img src = "/assets/images/SQL DB/set_pk.png" width = "80%" height = "80%">

체크를 해주면 id 왼쪽에 있는 아이콘이 열쇠 모양으로 바뀌는데, 이는 id가 primary key라는 것을 알려준다. 이렇게 바꾼 설정을 적용하려면 우측 하단의 Apply 버튼을 눌러주면, id column이 member 테이블의 primary key로 설정된다.

## 4. Primary key의 종류

Primary Key는 크게 Natural Key와 Surrogate Key로 구분할 수 있다.

Natural Key: 어떤 개체가 갖고 있는 속성을 나타내는 column이 Primary Key가 됐을 때 이를 Natural Key 라고 한다. 내가 만든 테이블에서 만약 email을 pk로 설정했다면 pk가 Natural Key인 것이다.

Surrogate Key: 앞서 설정한 id column같은 pk를 의미한다. id는 어떤 member의 속성을 직접적으로 나타내는 column은 아니다. 그저 pk로 사용하기 위해 인위적으로 생성한 column이다. 이처럼 개체의 실제 속성은 아니지만 pk로 쓰기 위해 추가한 column을 Surrogate Key 라고 한다.

## 5. NOT NULL 의 의미

앞서 id를 Primary Key로 설정하면서 PK 체크박스에 체크를 했는데, 이 때 NN도 같이 체크가 된 모습을 볼 수 있다. 이 NN은 NOT NULL의 줄임말이다. primary key는 항상 NOT NULL이어야 한다.

NULL: 특정 column에서 값이 존재하지 않는 상태를 나타낸다.

NN은 이 column에는 반드시 어떤 값이 들어있어야 함을 의미한다.<br>
이렇게 NOT NULL이 설정된 column에 NULL이 들어가게 될 row를 추가하려고 하면 DB에서 에러를 내서 그런 row가 추가될 수 없게 한다.

## 6. Primary Key와 Auto Increment 속성

우리는 Primary Key로 인위적으로 추가한 id는 Surrogate Key라고 했는데, Surrogate Key는 보통 1부터 시작해서 1씩 증가하는 정수값을 갖는다.

그렇다면 매번 새롭게 추가되는 row의 id는 이전 row의 id보다 1이 큰 정수가 되어야 할텐데,<br>
대부분의 DBMS에는 매번 새로운 row가 추가될 때마다 id에 이전보다 1이 큰 정수를 자동으로 넣어주는 기능이 있다.

<img src = "/assets/images/SQL DB/auto_increment.png" width = "80%" height = "80%">

위와 같이 AI(Auto Increment)에 체크를 해주고 적용해주면 row를 추가할 때 id를 사용자가 직접 지정해줄 필요가 없다.

## 7. 날짜 관련 column은 DATE 타입

column에 보면 birthday나 sign_up_day처럼 날짜 관련 정보를 담고 있는 column이 있는데,<br>
이런 column은 Datatype을 DATE로 설정해주면 이후 날짜 관련 계산에서 편리하게 이용할 수 있다.