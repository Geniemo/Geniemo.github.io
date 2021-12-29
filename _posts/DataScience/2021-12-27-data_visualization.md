---
title:  "[Data Science] 데이터 분석과 시각화"
excerpt: "데이터 분석과 시각화"

categories:
  - Data Science

toc: true
toc_sticky: true
toc_label: "데이터 분석과 시각화"

last_modified_at: 2021-12-27
---

## 시각화와 그래프

이번에는 데이터를 시각화해보겠습니다.

시각화가 중요한 이유는 크게 두가지가 있는데요,<br>
첫번째로, 시각화는 데이터를 분석하는 데에 도움을 줍니다.<br>
두번째로, 시각화는 리포팅에 도움을 줍니다.

이제 가장 기본적인 그래프 몇 가지를 살펴보도록 하겠습니다.

> 선 그래프

<script src="https://gist.github.com/Geniemo/fecec296ad18c2cb28421411f397a4be.js"></script>

> 막대 그래프

<script src="https://gist.github.com/Geniemo/f0ebe5546ccab6ddabdb3d3c380fa56c.js"></script>

> 파이 그래프

<script src="https://gist.github.com/Geniemo/563b8a6df9ff76a20389d3f7236719a7.js"></script>

> 히스토그램

<script src="https://gist.github.com/Geniemo/5cc9fc3313f4331c4e78cdc695629656.js"></script>

> 박스 플롯

<script src="https://gist.github.com/Geniemo/a5029462360515432d5266a153dc3339.js"></script>

> 산점도

<script src="https://gist.github.com/Geniemo/bef0ac3aa08bb1b2e1bea6ce681aebc7.js"></script>

## seaborn 시각화

seaborn이라는 라이브러리를 이용해서 그래프를 그릴 수 있는데,<br>
seaborn을 사용하면 더 많은 그래프를, 더 멋지게 그려낼 수 있습니다.<br>
그렇게 되면 같은 데이터로부터 더 좋은 insight를 얻게 될 수도 있습니다.

> KDE Plot

<script src="https://gist.github.com/Geniemo/956443fb55ddca2dcaf4729bb1f1b1ad.js"></script>

> LM Plot

<script src="https://gist.github.com/Geniemo/0cb6bd438ec71403ec09f6459a1e709f.js"></script>

> 카테고리별 시각화

<script src="https://gist.github.com/Geniemo/f082326cade70e4b3db4c3b967c5c170.js"></script>

> 상관 계수 시각화

<script src="https://gist.github.com/Geniemo/e4e18dd621b298dc1eca43aff15a74e4.js"></script>

## EDA

EDA(Exploratory Data Analysis)는 주어진 데이터를 다양한 관점에서 살펴보고 탐색하면서 인사이트를 찾는 것입니다.<br>
EDA에는 공식이 없습니다.<br>
시각적 기법이든 통게적 기법이든 다양한 방법으로 데이터를 살펴보는 것입니다.

codeit 강의에서 제공해주는 데이터로 한 번 EDA를 해보겠습니다.

이 데이터는 147개의 column을 가지고 있고, 997개의 row가 있습니다.<br>
147개의 컬럼은 아래와 같이 구성되어 있습니다.

- 0 ~ 18: 음악 취향
- 19 ~ 30: 영화 취향
- 31 ~ 62: 취미/관심사
- 63 ~ 72: 공포증
- 73 ~ 75: 건강 습관
- 76 ~ 132: 성격, 인생관 등
- 133 ~ 139: 소비 습관
- 140 ~ 146: 기본 정보

이런 데이터를 대상으로 뭘 분석해보기 전에 기본 정보들부터 분석해보도록 하겠습니다.

> 기본 정보 파악하기

<script src="https://gist.github.com/Geniemo/afceebf6039c7c3b8be7e8495e0ac22c.js"></script>

설문에 참여한 사람들에 대해 어느정도 파악을 했으니 이제 직접적인 분석을 해보겠습니다.

> 상관 관계 분석 (Correlation Analysis)

<script src="https://gist.github.com/Geniemo/06934d94884a13348bc6fc3584b01e44.js"></script>

> 클러스터 분석 (Cluster Analysis)

<script src="https://gist.github.com/Geniemo/5ff96c1149d717e19eac3c6814dd25af.js"></script>

## 새로운 인사이트 발견하기

> 새로운 값 계산하기

<script src="https://gist.github.com/Geniemo/bad69872383389bba83e933e823a7f96.js"></script>

> 문자열 필터링

<script src="https://gist.github.com/Geniemo/4f2380d36437ba1d93d3dbf872cffd2f.js"></script>

> 문자열 분리

<script src="https://gist.github.com/Geniemo/1cdb2b01a659fc688f7848f7d54c3509.js"></script>

> 카테고리로 분류

<script src="https://gist.github.com/Geniemo/4a83664f2be5858a21a5ceb208d2a0ad.js"></script>

> groupby

<script src="https://gist.github.com/Geniemo/cbe862b8dfa5b8047e55d457dcc6987a.js"></script>

> 데이터 합치기

<script src="https://gist.github.com/Geniemo/8caf4e6ad7558d4230755b99ac9752b1.js"></script>