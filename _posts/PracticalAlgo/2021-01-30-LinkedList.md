---
title:  "Linked List"
excerpt: "야매 연결 리스트"

categories:
  - 실전 알고리즘

toc: true
toc_label: "목차"

last_modified_at: 2021-01-30
---

## 연결 리스트의 성질
1. K번째 원소를 확인하기 위하여 O(K)가 필요
2. 임의의 위치에 원소를 추가/제거하기 위하여 O(1)이 필요
3. 원소들이 메모리 상에 연속하여 존재하지 않아 Cache hit rate가 낮지만 할당이 다소 쉬움.

## 배열 VS 연결 리스트
<table>
  <thead>
    <tr>
      <th style="text-align: left" width="150"> </th>
      <th style="text-align: center" width="70">배열</th>
      <th style="text-align: center" width="70">연결 리스트</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: left">K번째 원소에 접근</td>
      <td style="text-align: center">O(1)</td>
      <td style="text-align: center">O(K)</td>
    </tr>
    <tr>
      <td style="text-align: left">임의 위치에 원소 추가/제거</td>
      <td style="text-align: center">O(N)</td>
      <td style="text-align: center">O(1)</td>
    </tr>
    <tr>
      <td style="text-align: left">메모리 상의 배치</td>
      <td style="text-align: center">연속</td>
      <td style="text-align: center">불연속</td>
    </tr>
  </tbody>
</table>

<i style="color: #FF4500;">연결 리스트는 배열에 비해 임의 위치에 원소를 추가 또는 제거가 자주 필요할 때에 사용합니다.</i>

## 야매 연결 리스트 
대다수의 코딩 테스트에서는 C++ STL을 이용한다면 문제가 없겠지만, 아주 간혹 코딩 테스트에서 STL을 허용하지 않을 수 있습니다.<br>
그런 경우에 노드 구조체나 클래스를 이용한 정석적인 구현을 하기에는 힘들 수 있으니 아래 링크에 있는 야매 연결 리스트를 이용하시면 됩니다.<br>

야매 연결 리스트 <https://github.com/GenieWonimanimo/PracticalAlgo/blob/master/LinkedList.cpp>