---
title:  "[Data Science] 데이터 퀄리티 높이기"
excerpt: "데이터 퀄리티 높이기"

categories:
  - Data Science

toc: true
toc_sticky: true
toc_label: "데이터 퀄리티 높이기"

last_modified_at: 2021-12-30
---

## 데이터 퀄리티의 중요성

데이터 분석을 시작하기 전에 좋은 퀄리티의 데이터를 사용하는 게 우선입니다.<br>
분석할 때 안 좋은 데이터를 분석하면 안 좋은 결과가 나올 가능성이 높습니다.

대부분의 경우에는 우리에게 주어진 데이터는 완벽하지 않습니다.<br>
우리는 좋은 데이터가 뭔지 판단할 수 있어야 하고,<br>
마음에 들지 않는 데이터가 있으면 그 데이터의 퀄리티를 높이는 법을 알아야 합니다.

## 좋은 데이터의 기준

좋은 데이터의 기준을 얘기해보고 아래 데이터 클리닝에서<br>
데이터 퀄리티를 높여보겠습니다.

> 완결성: 필수적 데이터는 모두 기록되어 있어야 함

완결성은 결측값이 있는지 확인하면 됩니다.<br>
결측값이 존재하면 완결성이 없는 데이터셋입니다.

pandas DataFrame에서 결측값은 NaN으로 표시됩니다.

> 유일성: 동일한 데이터가 불필요하게 중복되어 있으면 안됨

> 통일성: 데이터가 동일한 형식으로 저장되어 있어야 함

> 정확성: 데이터가 정확해야 함

## 데이터 클리닝

> 완결성

<script src="https://gist.github.com/Geniemo/0cd45d05c0056acec90c50d597acb512.js"></script>

> 유일성

<script src="https://gist.github.com/Geniemo/7e37c43f81c779eb9b6abfbd0f7e1b3a.js"></script>

> 정확성

<script src="https://gist.github.com/Geniemo/b4ac1fecf2e6532dd6cf7590db421efd.js"></script>

<script src="https://gist.github.com/Geniemo/6073448870e780057a9d32e68c8269d8.js"></script>