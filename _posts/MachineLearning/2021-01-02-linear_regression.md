---
title:  "[Machine Learning] 선형 회귀"
excerpt: "Linear regression"

categories:
  - Machine Learning

toc: true
toc_sticky: true
toc_label: "선형 회귀"

last_modified_at: 2022-01-02
---

## 선형 회귀(Linear Regression)란?

선형 회귀는 머신러닝에서 가장 단순하기도 하면서 대표적인 알고리즘으로,<br>
종속 변수 y와 한 개 이상의 독립 변수 X와의 선형 상관 관계를 모델링하는 회귀분석 기법입니다.

좀 더 쉽게 말하면 주어진 데이터로부터<br>
x와 y의 관계를 가장 잘 나타내는 직선을 그리는 것을 말합니다.

선형회귀는 프로그램에게 답을 알려 주면서 학습을 시키기 때문에 지도 학습 알고리즘에 속합니다.

그럼 선형 회귀에 대해 알아보기 전에 먼저 선형 회귀 용어부터 살펴보겠습니다.

## 선형 회귀 용어

- 학습 데이터: 프로그램을 학습시키기 위해 사용하는 데이터
- 목표 변수: 맞추려고 하는 값 (target variable, output variable이라고도 합니다.)
- 입력 변수: 맞추는 데 사용하는 값 (input variable, feature라고도 합니다.)

보통 데이터를 표현할 때,<br>
학습 데이터의 개수를 m,<br>
i번 데이터의 x를 x<sup>(i)</sup>,<br>
i번 데이터의 y를 y<sup>(i)</sup>이라고 표현합니다.

## 가설 함수

선형 회귀에서 우리가 해야 하는 것은 데이터가 있을 때 최적선을 찾는 것입니다.<br>
우리는 최적선을 찾아내기 위해 다양한 함수를 시도해봐야 할텐데,<br>
이렇게 시도해보는 함수들을 가설 함수(hypothesis function)라고 합니다.

