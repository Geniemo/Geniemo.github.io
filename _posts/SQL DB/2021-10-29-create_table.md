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

<img src = "/assets/images/SQL DB/csv_contents.png" width = "40%" height = "40%">

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

<img src = "/assets/images/SQL DB/table_overview.png" width = "40%" height = "40%">

