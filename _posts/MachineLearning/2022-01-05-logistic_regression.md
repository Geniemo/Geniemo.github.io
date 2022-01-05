---
title:  "[Machine Learning] 로지스틱 회귀"
excerpt: "Logistic Regression"

categories:
  - Machine Learning

toc: true
toc_sticky: true
toc_label: "로지스틱 회귀"

last_modified_at: 2022-01-05
---

## 로지스틱 회귀

선형 회귀를 이용해서 분류를 할 수 있긴 하지만<br>
선형 회귀는 예외적 데이터에 너무 민감합니다.

그래서 분류를 할 때는 보통 선형 회귀 대신 로지스틱 회귀를 이용합니다.

선형 회귀는 데이터에 가장 잘 맞는 일차 함수를 찾는 것이고,<br>
로지스틱 회귀는 데이터에 가장 잘 맞는 시그모이드 함수를 찾는 것입니다.

시그모이드 함수는 아래와 같이 쓰고,

\\\[ \\displaystyle sigmoid(x) = \\frac{1}{1 + e^{-x}} \\\]

그래프는 아래와 같습니다.

<script src="https://gist.github.com/Geniemo/74cecbf3eb8f0ea1e797d2f3f36f0d41.js"></script>

시그모이드 함수는 무조건 0과 1 사이의 값만 반환합니다.<br>
그러니까, x가 아무리 커도, 아무리 작아도 0과 1사이의 값만 반환합니다.

결과가 0과 1 사이라는 것은 어떤 의미일까요?<br>
선형회귀에서 썼던 일차함수 같은 경우에는 결과가 얼마든지 크거나 작아질 수 있어 분류를 할 때 적합하지 않습니다.<br>
시그모이드 함수는 x값에 관계없이 항상 0과 1 사이의 값을 반환해서 분류를 할 때 적합합니다.

그런데, 로지스틱 회귀에서 사용할 시그모이드 함수는 분류에 적합하다고 해놓고<br>
왜 이름이 로지스틱 회귀일까요?

따지고 보면 시그모이드 함수의 결과값도 0과 1 사이의 연속적인 값이기 때문에 회귀라고 부를 수 있습니다.<br>
그래서 로지스틱 분류가 아니라 회귀라고 부르는 것인데요,<br>
우리는 시그모이드 함수의 결과값이 0.5보다 큰지 작은지를 보고 결국 분류를 합니다.<br>
따라서 이름은 회귀이지만 사용하는 건 주로 분류라는 점을 꼭 기억해야 합니다.

<script src="https://gist.github.com/Geniemo/74cecbf3eb8f0ea1e797d2f3f36f0d41.js"></script>

## 로지스틱 회귀 가설 함수

로지스틱 회귀에서 사용할 가설 함수를 알아보겠습니다.

선형 회귀에서는 가설 함수가 이렇게 생겼었습니다.

\\\[ h\_{\\theta}(x) = \\theta\_{0}x\_{0} + \\theta\_{1}x\_{1} + \\dots + \\theta\_{n}x\_{n} \\\]

그리고 벡터를 사용하면 더 간단하게도 표현할 수 있었습니다.

\\[ h\_{\\theta}(x) = \theta^{T}X \\]

이 포스트에서는 두 번째 형태의 함수를 주로 사용하겠습니다.

이 함수를 조금만 변형하면 로지스틱 함수의 가설 함수가 나옵니다.<br>
로지스틱 회귀의 가설 함수를 \\( h_{\theta}(x) \\)라고 해줘야하니까<br>
선형 회귀의 가설 함수를 \\( g_{\theta}(x) \\)라고 하겠습니다.

그러고 나면 로지스틱 회귀의 가설 함수는 이렇게 쓸 수 있습니다.

\\[ \displaystyle h_{\theta}{x} = \frac{1}{1 + e^{-g_{\theta}(x)}} = \frac{1}{1 + e^{-\theta^{T}x}} \\]

\\( g_{\theta}(x) \\)는 일차함수입니다.<br>
따라서 아웃풋이 엄청 크거나 작아질 수 있습니다.

그런데 로지스틱 회귀를 할 때 아웃풋이 항상 0과 1 사이에 있도록 하고 싶습니다.<br>
따라서 어떤 인풋을 넣든 간에 항상 아웃풋이 0과 1 사이에 있는 시그모이드 함수를 쓰는 것입니다.

로지스틱 회귀에서도 마찬가지로 목적은<br>
데이터에 가설 함수가 가장 잘 맞도록 \\(\theta\\)값들을 조절하는 것이므로 어렵게 생각할 필요는 없습니다.

## 결정 경계 (Decision Boundary)

결정 경계는 말 그대로 데이터를 분류하는 결정 경계선을 의미합니다.<br>
예를 들어 공부 시간에 따라 시험에 합격할 확률이 50% 이상이라면 합격, 50% 미만이라면 탈락이라고 할 때,<br>
\\( sigmoid(공부 시간)\\)이 0.5인 공부 시간이 100시간일 때<br>
분류를 구별하는 경계는 100시간입니다.

이렇게 분류를 할 때, 분류를 구별하는 경계선을 결정 경계라고 합니다.

## 로그 손실

가설 함수를 데이터에 잘 맞게 조절하기 위해서는 평가하는 기준이 있어야 하는데,<br>
그 기준이 되는 것이 손실 함수입니다.

로지스틱 회귀에서도 데이터에 잘 맞는 가설 함수를 찾는 것이고,<br>
이를 평가할 손실 함수가 필요합니다.

로지스틱 회귀의 손실 함수는 평균 제곱 오차를 사용하지 않습니다.<br>
대신 로그 손실(log-loss / cross entropy)를 사용합니다.<br>
로그 손실 함수의 수식은 아래와 같습니다.

$ logloss(h_{\theta}(x), y) = 
\begin{cases}
-log(h_{\theta}(x)), & y = 1 \newline
-log(1 - h_{\theta}(x)), & y = 0 
\end{cases}$

로그 손실 함수의 그래프는 아래와 같습니다.

<script src="https://gist.github.com/Geniemo/447e432de68bcf608159fdf5ebf43cd7.js"></script>

## 로지스틱 회귀 손실 함수

이제 이 로그 손실을 이용해서 로지스틱 회귀의 손실 함수를 만들어야 하는데,<br>
보통 로지스틱 회귀에서 로그 손실을 사용할 때에는 아래와 같이 씁니다.

\\[ logloss(h_{\theta}(x), y) = -ylog(h_{\theta}(x)) - (1 - y)log(1 - h_{\theta}(x)) \\]

다르게 보이지만 위에서 봤던 로그 손실 함수와 아예 똑같은 식입니다.<br>
\\(y\\)에 1을 대입하면 \\( -y\log(h_{\theta}(x)) \\)이고,<br>
0을 대입하면 \\( -log(1 - h_{\theta}(x)) \\)이 나옵니다.<br>
따라서, 그냥 로그 손실 함수를 한 줄에 표현한 것을 알 수 있습니다.

그럼 진짜 손실 함수를 한 번 보겠습니다.<br>
우리가 하려는 건 각 데이터에 대해 손실을 구한 후 손실의 평균을 내는 것입니다.<br>
이를 수식으로 나타내면 아래와 같습니다.

\\[ \displaystyle J(\theta) = \frac{1}{m}\sum_{i=1}^{m}[logloss(h_{\theta}(x^{(i)}), y^{(i)})] \\]

## 로지스틱 회귀 경사 하강법

가설 함수와 손실 함수는 선형 회귀와 달라졌지만<br>
경사 하강법을 하는 방법은 선형 회귀와 거의 똑같습니다.

선형 회귀든 로지스틱 회귀든 경사 하강법을 쓸 때는 항상 이렇게 합니다.

\\[ \displaystyle \theta = \theta - \alpha\frac{\partial}{\partial\theta}J(\theta) \\]

편미분을 하면 아래와 같은 식이 나옵니다.

\\[ \displaystyle \theta_{j} = \theta_{j} - \alpha\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x)^{(i)} - y^{(i)}) \cdot x_{j}^{(i)} \\]

경사 하강법을 할 때의 수식을 선형대수학을 이용해서 간단하게 표현해보겠습니다.

\\[ X = \left[
\begin {array}{cccc}
    x_{0}^{(1)} & x_{1}^{(1)} & \dots & x_{n}^{(1)} \newline
    x_{0}^{(2)} & x_{1}^{(2)} & \dots & x_{n}^{(2)} \newline
    \vdots & & & \newline
    x_{0}^{(m)} & x_{1}^{(m)} & \dots & x_{n}^{(m)} \newline
\end {array}
\right],
\theta = \left[
\begin {array}{c}
\theta_{0} \newline
\theta_{1} \newline
\vdots \newline
\theta_{n} \newline
\end {array}
\right],
y = \left[
\begin {array}{c}
y_{0} \newline
y_{1} \newline
\vdots \newline
y_{m} \newline
\end {array}
\right] \\]일 때,

\\( sigmoid(X\theta) \\)가 가설 함수의 예측값이고,<br>
\\( sigmoid(X\theta) - y \\)가 예측 값과 목표 변수의 차이입니다.

이를 이용하여 \\(\theta\\)의 변화를 수식으로 나타내면 아래와 같습니다.

\\[ \displaystyle \theta \leftarrow \theta - \alpha\frac{1}{m}(X^{T} \times (sigmoid(X\theta) - y)) \\]

## 분류가 3개 이상일 때

A, B, C의 세 카테고리로 데이터를 분류해야 한다고 가정하겠습니다.

처음에는 문제를 단순화해서 A인지 아닌지만 분류합니다.<br>
이렇게 학습시켜서 얻은 가설 함수를 \\( h_{theta}^{(0)}(x) \\)라고 하겠습니다.

그 다음에는 B인지 아닌지만 분류합니다.
이렇게 학습시켜서 얻은 가설 함수를 \\( h_{theta}^{(1)}(x) \\)라고 하겠습니다.

마지막으로 C인지 아닌지를 분류합니다.
이렇게 학습시켜서 얻은 가설 함수를 \\( h_{theta}^{(2)}(x) \\)라고 하겠습니다.

이렇게 3개의 가설 함수를 얻었습니다.<br>
이제 주어진 데이터들의 입력 변수들을 세 개의 가설 함수에 각각 넣습니다.

그러면 각각의 데이터가 A, B, C일 확률을 모두 구할 수 있습니다.<br>
여기서 가장 확률이 높은 카테고리로 분류해주면 됩니다.

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script><script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## scikit-learn을 이용한 간단한 로지스틱 회귀

<script src="https://gist.github.com/Geniemo/ca3d915b2e7a88e88bc69b0c6a37fa85.js"></script>