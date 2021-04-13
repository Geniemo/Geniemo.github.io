---
title:  "Linked List"
excerpt: "야매 연결 리스트"

categories:
  - Practical Algo

toc: true
toc_label: "Linked List"

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
      <th style="text-align: left" width="250"> </th>
      <th style="text-align: center" width="120">배열</th>
      <th style="text-align: center" width="120">연결 리스트</th>
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

```cpp
#include <bits/stdc++.h>
using namespace std;

const int MX = 1000005;
int dat[MX], pre[MX], nxt[MX];
int unused = 1;

void insert(int addr, int num){ // addr 번지 뒤에 num을 추가
    dat[unused] = num;
    pre[unused] = addr;
    nxt[unused] = nxt[addr];
    if (nxt[addr] != -1) pre[nxt[addr]] = unused;
    nxt[addr] = unused;
    unused++;
}
 
void erase(int addr){ // addr 번지의 원소를 제거
    nxt[pre[addr]] = nxt[addr];
    if (nxt[addr] != -1) pre[nxt[addr]] = pre[addr];
}

void traverse(){
  int cur = nxt[0];
  while(cur != -1){
    cout << dat[cur] << ' ';
    cur = nxt[cur];
  }
  cout << "\n\n";
}

void insert_test(){
  cout << "****** insert_test *****\n";
  insert(0, 10); // 10(address=1)
  traverse();
  insert(0, 30); // 30(address=2) 10
  traverse();
  insert(2, 40); // 30 40(address=3) 10
  traverse();
  insert(1, 20); // 30 40 10 20(address=4)
  traverse();
  insert(4, 70); // 30 40 10 20 70(address=5)
  traverse();
}

void erase_test(){
  cout << "****** erase_test *****\n";
  erase(1); // 30 40 20 70
  traverse();
  erase(2); // 40 20 70
  traverse();
  erase(4); // 40 70
  traverse();
  erase(5); // 40
  traverse();
}

int main(void) {
  fill(pre, pre+MX, -1);
  fill(nxt, nxt+MX, -1);
  insert_test();
  erase_test();
}
```

## 활용 예제
연결 리스트를 활용한 문제는 심하게 어려운 응용문제들은 출제하기가 어렵고 텍스트 에디터와 같은 전형적 문제들이 출제가 됩니다.<br>
아래 문제를 연결 리스트를 이용하여 풀어보면 도움이 됩니다.

백준 1406번 <https://www.acmicpc.net/problem/1406>

```cpp
#include <bits/stdc++.h>
using namespace std;

const int MX = 1000005;
char dat[MX];
int pre[MX], nxt[MX];
int unused = 1;

void insert(int addr, char item){ // addr 번지 뒤에 num을 추가
    dat[unused] = item;
    pre[unused] = addr;
    nxt[unused] = nxt[addr];
    if (nxt[addr] != -1) pre[nxt[addr]] = unused;
    nxt[addr] = unused;
    unused++;
}

void erase(int addr){ // addr 번지의 원소를 제거
    nxt[pre[addr]] = nxt[addr];
    if (nxt[addr] != -1) pre[nxt[addr]] = pre[addr];
}

void traverse(){
  int cur = nxt[0];
  while(cur != -1){
    cout << dat[cur];
    cur = nxt[cur];
  }
}

int main(void)
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);

    fill(pre, pre + MX, -1);
    fill(nxt, nxt + MX, -1);

    int cur = 0;
    string str;
    cin >> str;
    for (auto c : str)
    {
        insert(cur, c);
        cur++;
    }

    int M;
    cin >> M;
    for (int i = 0; i < M; i++)
    {
        char option;
        cin >> option;
        switch (option)
        {
        case 'L': // 왼쪽으로 커서 이동
            if (pre[cur] != -1)
                cur = pre[cur];
            break;
        case 'D': // 오른쪽으로 커서 이동
            if (nxt[cur] != -1)
                cur = nxt[cur];
            break;
        case 'B': // 왼쪽에 있는 것 삭제
            if (pre[cur] != -1)
            {
                erase(cur);
                cur = pre[cur];
            }
            break;
        case 'P': // 왼쪽에 문자 삽입
        {
            char c;
            cin >> c;
            insert(cur, c);
            cur = nxt[cur];
        }
        }
    }
    traverse();
    return 0;
}
```