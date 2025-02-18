---
title: "자료구조"
date: 2023-03-02
tags: ["CS"]
---

## 제 1장 : 자료구조를 배우기 위한 준비 (230302)

### 배열

- 배열(Array): 동일한 타입의 원소들이 **연속적인 메모리 공간**에 할당되어 있는 기초적인 자료구조

### 추상데이터 타입

- 추상데이터타입(**ADT**:Abstract Data Type) : 데이터와 그 데이터에 대한 추상적인 연산들로써 구성
- ADT =~ 자바의 interface, 자료구조 =~ 자바의 class
- 자료구조는 추상데이터타입을 구체적으로 구현한 것

## 1-2 수행시간의 분석

- 알고리즘의 성능: 수행시간을 나타내는 **시간복잡도(Time Complexity)**와 알고리즘이 수행되는 동안 사용되는 메모리 공간의 크기를 나타내는 **공간복잡도(Space Complexity)**에 기반하여 분석

* 시간 복잡도

  - 시간복잡도는 알고리즘(연산)이 실행되는 동안에 사용된 기본적인 연산 횟수를 입력 크기의 함수로 나타낸다.
  - 기본 연산(Elementary Operation)이란 데이터 간 크기 비교, 데이터 읽기 및 갱신, 숫자 계산 등과 같은 단순한 연산을 의미

* 4가지 종류의 분석

  - 최악경우 분석(Worst-case Analysis) : 상한선의 의미
  - 평균경우 분석(Average-case Analysis)
  - 최선경우 분석(Best-case Analysis) : 가장 빠른 수행시간
  - 상각분석(Amortized Analysis) : 총 연산횟수를 합하고 연산 횟수로 나누어 수행시간을 분석

## 1-3 수행시간의 점근표기법

- O (Big-Oh)-표기법
- Ω (Big-Omega)-표기법
- Θ (Theta)-표기법

### O (Big-Oh) 표기법

- 모든 N ≥ N0에 대해서 f(N) ≤ cg(N)이 성립하는 양의 상수 c와N0가 존재하면, f(N) = O(g(N))이다. 모든 N ≥ N0에 대해서 f(N) ≤ cg(N)이 성립하는 양의 상수 c와 N0가 존재하면, f(N) = O(g(N))

* f(N) = O(g(N))은 N0 보다 큰 모든 N 대해서 f(N)이 양의 상수를 곱한 g(N)에 미치지 못한다는 뜻
* g(N)은 f(N)의 **상한(Upper Bound)** 이라고 한다

### Ω (Big-Omega) 표기법

- 모든 N ≥ N0에 대해서 f(N) ≥ cg(N)이 성립하는 양의 상수 c와 N0가 존재하면, f(N) = Ω(g(N))
- f(N) = Ω(g(N))은 양의 상수를 곱한 g(N)이 f(N)에 미치지 못한다는 뜻
- g(N)을 f(N)의 **하한(Lower Bound)** 이라고 한다

### Θ (Theta) 표기법

- 모든 N ≥ N0에 대해서 c1g(N) ≥ f(N) ≥ c2g(N)이 성립하는 양의 상수 c1, c2, N0가 존재하면, f(N) = Θ(g(N))
- Θ-표기는 수행시간의 O-표기와 Ω-표기가 동일한 경우에 사용

### 자주 사용되는 함수의 O-표기와 이름

- O(1), O(logN), O(N), O(NlogN), O(N2), O(N3), O(2N)

## 1-5 순환 (Recursion)

### 순환으로 구현된 메소드의 구성요소

- 기본(Base) case : 스스로를 더 이상 호출하지 않는 부분
- 순환 case : 스스로를 호출하는 부분

### 꼬리 순환 (Tail Recursion)

- 메소드의 마지막 부분에서 순환 (호출 후 되돌아 왔을때 수행할 연산이 없는 경우)
- 꼬리 순환은 반복문으로 변환하는 것이 효율적이다

```java
public class TailRecursion {
  public static int factorial(int n, int fact) {
    if (n==1)
      return fact;
    return factorial( ,);
  }
}
```

## 제 2장 : 리스트

### 리스트

- 일련의 동일한 타입의 항목들이 나열된 것

### 배열

- 동일한 타입의 원소들이 연속적인 메모리 공간에 할당되어 각 항목이 하나의 원소에 저장되는 기본적인 자료구조
- 접근 : O(1), 삽입/삭제 : O(n)

### 배열로 리스트 구현 (ArrList)

- peek, insert, resize, delete

### 단순 연결 리스트(Singly Linked List)

- print, search, insertFront, insertAfter

* 자기참조변수
  ```java
  public class Node <E> {
    private Node<E> next; // 자기 참조 변수
    ...
  }
  ```
* 수행시간
  - search : O(n)
  - insert, delete : O(1), p가 안주어지면 O(n)

### 이중 연결 리스트 (Doubly Linked List)

- head, tail, item
- insertBefore, insertAfter, delete,

* 수행시간
  - 삽입/삭제 연산 : O(1)
  - 탐색 연산 : O(n)

### 원형 연결 리스트(Circular Linked List)

- 수행시간
  - 삽입/삭제 연산 : O(1)
  - 탐색 연산 : O(n)

## 제 3장 : 스택과 큐

### 스택

- 배열로 구현 / LinkedList로 구현
- 후위 표기 <-> 중위 표기
- 수행시간
  - push, pop : O(1)
  - 배열 크기의 확대/축소 : O(n)
  - 단순 연결 리스트의 pop, push : O(1)

## 제 4장 : 트리

### 용어

- root, parent, child
- leaf, sibling, ancesto리(조상), descendant(후손)
- subtree(노드 자신과 후손으로 구성된 트리)
- degree(차수 : 자식 수)
- level (깊이와 동일, 0 또는 1부터 시작)
- height (트리의 최대 level)
- key (탐색에 사용되는 노드에 저장된 정보)

### 왼쪽 자식-오른쪽 형제 (Left Child-Right Sibling) 표현

- 노드의 왼쪽 자식과 오른쪽 형제를 가리키는 2개의 레퍼런스만 사용

### 이진 트리 (Binary Tree)

- 각 노드의 자식 수가 2 이하인 트리

* 특별한 형태의 이진트리

  ![speical binary tree](/static/image/ds_speical_binary_tree.png)

  - 포화 이진 트리(Perfect Binary Tree)
    - 각 내부 노드가 2개의 자식을 가지고 모든 이파리가 같은 층에 있는 트리
  - 완전 이진 트리(Complete Binary Tree)
    - 마지막 레벨을 제외한 각 레벨이 노드들로 꽉 차있고, 마지막 레벨에는 노드들이 왼쪽부터 빠짐없이 채워진 트리

* 이진 트리의 속성

  - 레벨 k에 있는 최대 노드 수 = $2^{k-1}$
  - 높이가 h인 포화 이진 트리에 있는 노드 수 = $2^{h}-1$
  - n개의 노드를 가진 완전 이진 트리의 높이 = $log_{2}(n+1)$
  - 높이가 h인 완전 이진트리에 존재할 수 있는 노드 수 n

* 배열에 저장된 이진 트리

  - 트리

    ```text
    A
    ├── B
    │   ├-─ D
    │   │   ├── H
    │   │   └── I
    │   └-─ E
    │       ├── J
    │       └── K
    └── C
        ├── F
        └── G

    ```

- 위 트리를 배열에 저장하면 (인덱스 1부터 시작)

  ```text
  A = [A, B, C, D, E, F, G, H, I, J, K]
  ```

  - a[i]의 부모는 **a[i/2]**, 단 i>1
  - a[i]의 왼쪽 자식은 **a[2i]**, 단 2i <= n
  - a[i]의 오른쪽 자식은 **a[2i+1]**, 단 2i+1 <= n

- 편향(skewed) 이진 트리
  - 메모리 낭비가 심하다

### 이진 트리의 순회

preorder ; root - left - right
inorder : left - root - right
postorder : left - right - root
levelorder : left -> right (from top level)

### 수행 시간

- O(n) 시간이 소요

### 집합의 표현

- 배열
  | index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
  | - | - | - | - | - | - | - | - | - | - | - |
  | value | 4 | 2 | 7 | 7 | 4 | 4 | 2 | 7 | 7 | 4 |

* 집합 1

```text
7
├── 2
│   ├-─ 1
│   └-─ 6
├── 8
└── 3
```

- 집합2

```text
4
├── 0
├── 5
└── 9
```

- 수행 시간
  - union : O(N)
  - find : O(N)

## 제 5장 : 탐색 트리

### 5.1 이진탐색트리

#### min 함수

#### deleteMin 함수

#### delete 함수

- CASE 1 : 삭제할 노드의 두 자식이 모두 null
- CASE 2 : 삭제할 노드의 오른쪽 자식만 null
- CASE 3 : 삭제할 노드의 왼쪽 자식만 null
- CASE 4 : 삭제할 노드의 자식이 둘다 존재

### 시간 복잡도

- O($logn$)

### 5.2 AVL 트리

#### AVL트리의 정의

> 임의의 노드 x에 대해 x의 왼쪽 서브트리와 오른쪽 서브트리의 높이 차이가 1을 넘지 않는 이진 탐색 트리

#### AVL트리의 회전 연산

- LL 회전 : 왼쪽으로 치우친 경우 rotateRight(n)를 통해 해결
- RR 회전 : 오른쪽으로 치우친 경우 rotateLeft(n)를 통해 해결
- LR 회전 : rotateLeft(n.left) -> rotateRight(n)로 해결
- RL 회전 : rotateRight(n.right) -> rotateLeft(n)로 해결
- 4가지 회전의 공통점
  > 회전 후의 트리들이 모두 같다, 모두 O(1)

#### AVL트리의 연산

- 삽입 연산
  1. 이진 트리의 삽입과 동일하게 새 노드 삽입
  2. 새 노드로부터 루트로 거슬러 올라가며 불균형이 발생하면 적절하게 회전 연산 수행
- 삭제 연산

### 5.3 2-3 트리

#### 2-3 트리의 정의

> 임의의 노드가 2개 또는 3개의 자식을 가질 수 있는 트리로, 모든 리프 노드가 같은 레벨에 있다.

#### 2-3 트리의 연산

- 탐색 연산
  > 이진 탐색 트리와 동일한 방법으로 탐색
- 분리 연산
  > 키를 부모로 올려 보냄  
  > 부모가 3-노드이면 다시 분리연산 수행  
  > 루트에서 일어나면 트리의 높이 1 증가
- 삽입 연산
  > 삽입 후 분리 연산을 수행
- 삭제 연산
  > 삭제할 노드가 이파리 노드이면 그냥 삭제  
  > 삭제한 노드가 이파리 노드가 아니라면 교환 후 삭제
  > 이동 연산, 통합 연산 사용
- 이동 연산
  > 빈 자리를 형제와 바꾼다  
  > 이동연산이 불가능하면 통합 연산 수행
- 통합 연산
  > 삭제한 노드의 부모와 형제를 통합한다

#### 2-3 트리의 수행시간

- 탐색, 삽입, 삭제 연산 -> O($logn$) -> 트리의 높이에 비례
- 분리 연산, 통합 연산 -> O(1)
- 2-3트리가 가장 높은 경우 모든 노두가 2-노드인 경우
  > 높이 : $ log_2(n+1) $
- 2-3트리가 가장 낮은 경우 모든 노드가 3-노드인 경우
  > 높이 : $ log_3(n) $

### 5.4 2-3-4 트리

> 2-3트리를 확장한 2-3-4 트리는 노드가 자식을 4개까지 가질 수 있는 완전균형트리

- 이론적으로는 2-3트리와 동일하다 실제로는 더 빠름

### 5.5 B-트리

#### B-트리의 정의

> 다수의 키를 가진 노드로 구성되어 다방향 탐색이 가능한 균현트리

#### B-트리의 연산

- 탐색 연산
  > 루트 부터 시작 각 노드에서 이진 탐색 수행
- 삽입 연산
  > 이파리에 새 키를 수용할 공간이 있다면, 정렬된 상태를 유지하도록 삽입
  > 이미 M-1개의 키를 가지고 있으면, 분리 연산을 수행
- 삭제 연산
  > 삭제할 노드가 이파리 노드이면 그냥 삭제
  > 삭제한 노드가 이파리 노드가 아니라면 교환 후 삭제
  > 이동 연산, 통합 연산 사용
- 이동 연산
  > 키의 수가 M/2-1보다 작으면(underflow) 형제, 부모노드를 이능
  > 이동 연산이 불가능하면 통합 연산 수행
- 통합 연산
  > 삭제한 노드의 부모와 형제를 통합한다

#### B-트리의 수행시간

- 탐색, 삽입, 삭제 연산 -> O($log_{M/2}n$) -> 트리의 높이에 비례

## 제 6장 : 해시 테이블

#### 대표적인 해시 함수

- 중간 제곱 함수 : 키를 제곱한 후, 적절한 크기의 중간 부분을 사용
- 접기 함수 : 키를 여러 부분으로 나눈 후, 이들을 더한 값을 사용

#### 자바의 hashCode()

```java
private int hash(Key k) {
  return (k.hashCode() & 0x7fffffff) % M;
}
```

#### 해시 테이블의 저장 방식

- 개방 주소 방식 : 충돌된 키를 일정한 방식에 따라 찾아낸 empty원소에 저장
- 선형 조사, 이차조사, 이중해싱

#### 선형 조사 : 충돌이 일어난 곳으로부터 순차적으로 탐색

- 1차 군집화 (키들이 뭉쳐지는 현상) 발생
- 군집화는 군집된 키들을 순차적으로 방문해야하는 문제점을 일으킨다

## 제 7장 : 우선순위 큐

### 우선순위 큐 (Priority Queue)

- 가장 높은 우선순위를 가진 항목에 접근과 삭제, 임의의 우선순위를 가진 항목의 삽입을 지원하는 자료구조

### 힙 (Heap)

- 완전 이진 트리로서 부모의 우선순위가 자식의 우선순위보다 높은 자료구조
- 최소 힙, 최대 힙

### 힙의 연산

#### 최솟값 삭제

- 루트 삭제 후, 마지막 노드를 루트로 이동
- downheap 수행 : 루트부터 비교하면서 내려감

#### 삽입

- 마지막 항목의 다음에 삽입
- upheap 수행 : 루트로 비교하면서 올라감

### 상향식 힙

```java
public void createHeap() {
  for (int i = N/2; i>0; i--) {
    downheap(i);
  }
}
```

- O(n)

### 수행 시간

- 접근, 삽입, 삭제 : O(logn)

## 제 8장 : 정렬

### 선택 정렬 (Selection Sort)

- 항상 O(n^2)

### 삽입 정렬 (Insertion Sort)

- 최악 : O(n^2)
- 최선 : O(n) : 이미 정렬된 경우

### 힙 정렬 (Heap Sort)

- 항상 : O(nlogn)

### 합병 정렬 (Merge Sort)

- 항상 : O(nlogn)
- Stable Sort : 같은 값의 키를 가진 레코드의 순서가 정렬 후에도 유지되는 정렬

### 퀵 정렬 (Quick Sort)

- 최악 : O(n^2)
- 최선 : O(nlogn)

- 성능 향상 방법
  - Median of Three : 첫번째, 마지막, 중간값 중에서 중간값을 피벗으로 선택
  - 입력이 작은 크기가 되었을때 삽입 정렬을 사용
