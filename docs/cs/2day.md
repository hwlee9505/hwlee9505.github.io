---
layout: default
title: Week 2
parent: CS 지식
nav_order: 2
---

# 2주차 (자료구조 & 알고리즘) 
{: .no_toc }

---

![](/assets/images/cs/week2.jpeg)


## JAVA의 Collection클래스의 대표 인터페이스를 설명하시오

![](/assets/images/cs/week2_2.png)


컬렉션 클래스는 크게 list, set, map이 있습니다.   

list는 순차적인 데이터를 저장하며 중복을 허용하는 자료구조입니다.   
arraylist, linkedlist, stack, vactor가 하위 클래스로 존재합니다.  

set은 순서를 유지하지 않고 데이터의 중복을 허용하지 않는 자료구조입니다.  
hashset, treeset이 하위 클래스로 존재합니다.  

map은 키와 값으로 이루어진 데이터를 순서를 유지하지 않고 키의 중복만 허용하지 않는 자료구조입니다.  
hashmap, treemap, hashtable가 하위 클래스로 존재합니다.  
(map의 경우 collection 인터페이스를 상속받고 있지는 않지만 collection으로 분류된다.)

---

### (꼬리 질문) hashset과 treeset의 차이점은 무엇인가요? hashset과 treeset의 차이점은 무엇인가요?

hashset은 내부적으로 해싱을 이용해서 구현한 컬렉션이다.  
Hashset은 저장 순서를 유지하지 않으므로 저장 순서를 유지하려면 LinkedHashSet을 이용해야 한다.  

Treeset은 이진탐색트리의 형태로 데이터를 저장하는 컬렉션이다.  
이진탐색트리중에서도 성능을 향상시킨 레드블랙 트리로 구현되어있다.  
데이터의 추가,삭제에는 시간이 걸리지만 검색과 정렬이 뛰어나다는 특징이 있다.  
속도 : hashset > linkedhashset > treeset  

hashset과 treeset과 linkedhashset모두 thread-safe하지 않는다.  

hashset은 내부적으로 해싱을 이용해서 구현한 컬렉션이다.  
Hashset은 저장 순서를 유지하지 않으므로 저장 순서를 유지하려면 LinkedHashSet을 이용해야 한다.   

Treeset은 이진탐색트리의 형태로 데이터를 저장하는 컬렉션이다.  
이진탐색트리중에서도 성능을 향상시킨 레드블랙 트리로 구현되어있다.  
데이터의 추가,삭제에는 시간이 걸리지만 검색과 정렬이 뛰어나다는 특징이 있다.  
속도 : hashset > linkedhashset > treeset  

hashset과 treeset과 linkedhashset모두 thread-safe하지 않는다.

---

## 우선순위큐에 대해서 설명하시오

FIFO가 아니라 데이터를 근거로 우선순위를 판단, 우선순위가 높은 것을 먼저 가져온다.  

구현 방법(배열, 연결리스트, 힙)  

배열방법은 삽입,삭제,탐색 모두 O(N)이고 연결리스트는 탐색만 O(N)이고 삽입 삭제 모두 O(1)이다.  

주로 힙을 이용하여 우선순위 큐를 구현한다.  
힙은 완전이진트리의 성질을 만족하므로 1차원 배열로 표현이 가능하다.  
이를 통해 leaf node에 O(1)에 접근이 가능하다.  
데이터의 삽입은 leaf노드부터 시작한다.  
삽입 후 heapify 과정을 통해 힙의 모든 부모-자식 노드의 우선순위에 맞게 설정한다.(부모의 우선순위는 자식의 우선순위보다 커야한다.)  

삭제는 root 노드를 삭제하게 된다.  
삭제 후 마지막 leaf노드를 루트 노드로 옮긴 후 heapify 과정을 수행한다.  
FIFO가 아니라 데이터를 근거로 우선순위를 판단, 우선순위가 높은 것을 먼저 가져온다. 
구현 방법(배열, 연결리스트, 힙)  
배열방법은 삽입,삭제,탐색 모두 O(N)이고 연결리스트는 탐색만 O(N)이고 삽입 삭제 모두 O(1)이다.  
주로 힙을 이용하여 우선순위 큐를 구현한다.  
힙은 완전이진트리의 성질을 만족하므로 1차원 배열로 표현이 가능하다.  
이를 통해 leaf node에 O(1)에 접근이 가능하다.  
데이터의 삽입은 leaf노드부터 시작한다.  
삽입 후 heapify 과정을 통해 힙의 모든 부모-자식 노드의 우선순위에 맞게 설정한다.(부모의 우선순위는 자식의 우선순위보다 커야한다.)  
삭제는 root 노드를 삭제하게 된다.  
삭제 후 마지막 leaf노드를 루트 노드로 옮긴 후 heapify 과정을 수행한다.

---

## 트리와 그래프의 차이점에 대해서 설명하시오.  

트리 구조란 그래프의 일종으로 , 여러 노드가 한 노드를 가리킬 수 없는 구조이다.  
서로 다른 두 노드를 잇는 길이 하나뿐인 그래프를 트리라고 한다. (모든 자식 노드는 하나의 부모 노드를 가진다.)   

그래프는 일부 객체들의 쌍들이 서로 연관된 객체의 집합을 이루는 구조이다.  
일련의 꼭지점들과 그 사이를 잇는 변들로 구성된 조합론적 구조로 볼 수있다.  
트리에는 루트노드나 부모 자식 관계가 존재한다.  
트리는 DAG(Directed Acyclic Graph)로 사이클이 존재하지 않는 방향 그래프를 말한다.  

그래프는 각 노드 사이에 cycle을 형성할 수 있다.  
그래프는 방향그래프, 무방향 그래프가 있다.  
그래프는 self노드도 가질 수 있다.

---

## 완전 이진트리와 포화 이진트리의 차이점에 대해서 설명하시오.

완전 이진트리란 포화이진트리의 leaf들을 오른쪽에서부터 제거해서 얻어진 트리이다.  
포화 이진트리란 모든 leaf들의 레벨이 동일한 이진 트리이며, leaf가 아닌 내부노드들은 모두2개의 자식을 가지는 트리이다.  
높이가 h인 포화 이진 트리의 노드수는 2^(h+1) -1이 된다.  

완전 이진 트리의 높이가  h라면 노드의 수는 2^h이상이고 2^(h+1)개 미만이다.

---

## hash함수와 hashtable에 대해 설명하시오.

해시 함수(Hash Function)?  

데이터를 효율적으로 관리하기 위해 임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 함수이다.  
해시 테이블은 키(key)와 값(value)이 하나의 쌍을 이루는 데이터 구조이다.  
즉, 키(key)와 배열의 인덱스(index)를 이용하여 키를 저장하는 자료구조이다.  
해시 테이블은 키를 간단한 해시 함수(hash function)로 계산하여 그 값을 배열의 인덱스로 사용한다.  
해시 테이블은 해시 맵, 맵, 딕셔너리, 연관 배열 이라는 이름으로 알려져있다.  

입력 받은 Key -> hash 함수 -> hash code -> index -> value 넣기

해시 테이블 장점은 적은 리소스로 많은 데이터를 효율적으로 관리할 수 있고 검색, 삽입, 삭제가 빠르고 키와 해시값이 연관이 없어 보안에도 많이 사용된다.  
중복을 제거하는데 유리하다.  

단점은 충돌이 발생할 수 있고 공간 복잡도가 커지고 해시 함수 의존도가 높다는 점이다.  

---

### (꼬리 질문) 꼬리질문 hashtable의 탐색, 삽입, 삭제 시간복잡도에 대해 설명하시오.

최선인 경우 탐색, 삽입, 삭제 모두 O(1)이고, 최악의 경우 모두 O(N)이다.  

단순균등해싱의 경우 탐색, 삽입, 삭제 모두 O(1)이다.  
해시 함수(해시 함수의 성능은 무시한다)를 이용해서 원하는 인덱스에 탐색, 삽입, 삭제 하면 되므로 선형탐사, 제곱탐사, 이중해싱, 체이닝 모두 O(N)이다.  
선형탐사, 제곱탐사, 이중해싱 모두 최악의 경우에, 적재율이 1에 가까워지게 될 수 있는데 이 경우 모든 배열 원소를 탐사해야 하므로 이다.  

체이닝은 한 인덱스에 모든 key들이 몰릴 수 있으므로 연결리스트의 마지막까지 탐사해야 하는 경우가 발생할 수 있다.  

[관련 링크](https://ferrante.tistory.com/43){: .btn .fs-5 .mb-4 .mb-md-0 }

![](/assets/images/cs/week2_3.png)

[출처](http://contents.kocw.or.kr/KOCW/document/2012/kumoh/kimyeonghak/17.pdf){: .btn .fs-5 .mb-4 .mb-md-0 }