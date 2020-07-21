---
layout: default
title: linux에서 System Call 추가하기
parent: CS 지식
nav_order: 10
---

# [Kernel] linux-5.2.10에서 스택 push, pop 시스템콜(System Call) 추가하기
{: .no_toc }

## 리눅스 Kernel을 수정하여 새로운 System Call을 추가하고, 응용프로그램의 호출에 의해 동작을 확인하려 합니다.


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## 자료구조에서 set과 list의 차이는?

```scss
list : 순서가 중요 -> 중복 허용  
set  : 순서는 중요하지 않은데 -> 중복 허용 안됨
```

set : 순서 없음, 중복 데이터 불가(집합 성격)  
list : 순서 있음(index 사용 가능), 중복 허용  


## context-switching이란?

```scss
여러 스레드들이 짧게 짧게 서로 실행할 수 있는 시간을 줌으로써 같이 동작할수 있게끔 그렇게...  
```

문맥 교환(context switch)이란 하나의 프로세스가 CPU를 사용 중인 상태에서 다른 프로세스가 CPU를 사용하도록 하기 위해, 이전의 프로세스의 상태(문맥)를 보관하고 새로운 프로세스의 상태를 적재하는 작업을 말한다.  
한 프로세스의 문맥은 그 프로세스의 프로세스 제어 블록(PCB)에 기록되어 있다.  
(위키피디아)




## thread와 process중 어느것이 비용이 작은가?

프로세스는 독립된 메모리 공간을 가지지만, 스레드는 한 프로세스 내에서 메모리를 공 유하므로 비용이 더 작다.

[관련 링크](https://arer.tistory.com/80){: .btn .fs-5 .mb-4 .mb-md-0 }


## 다대다 테이블의 관계를 스키마로 어떻게 작성할래?

```scss
외래키를 통해서 두 테이블을 엮어서 만들 것입니다.
```

매핑 테이블을 사용한다

[관련 링크](https://siyoon210.tistory.com/26){: .btn .fs-5 .mb-4 .mb-md-0 }


## 리팩토링이란?

```scss
잘 모르겠습니다.
```

리팩터링(refactoring)은 소프트웨어 공학에서 '결과의 변경 없이 코드의 구조를 재조정함'을 뜻한다.  
주로 가독성을 높이고 유지보수를 편하게 한다.  
버그를 없애거나 새로운 기능을 추가하는 행 위는 아니다.  
사용자가 보는 외부 화면은 그대로 두면서 내부 논리나 구조를 바꾸고 개선하는 유지보수 행 위이다.  
(위키피디아)

## http와 https의 차이점?

```scss
HTTP는 클라이언트와 서버를 나눌 때 데이터를 통신할 때 사용하는 프로토콜  
HTTPS : 더 보안적으로 이루어진걸로 알고 있습니다.  
HTTP는 보안 적용되지 않았나 ? HTTP보다는 떨어지는 걸로 알고 있습니다.  
```

HTTPS(HyperText Transfer Protocol over Secure Socket Layer, HTTP over  
TLS,[1][2] HTTP over SSL,[3] HTTP Secure[4][5])는  
월드 와이드 웹 통신 프로토콜인 HTTP의 보안이 강화된 버전이다.  
HTTPS는 소켓 통신에서 일반 텍스트를 이용하는 대신에, SSL이나 TLS 프로토콜을 통해 세 션 데이터를 암호화한다.  
따라서 데이터의 적절한 보호를 보장한다.  
HTTPS의 기본 TCP/IP 포트는 443이다.  
HTTPS를 사용하는 웹페이지의 URI는 'http://'대신 'https://'로 시작한다.  
(위키피디아)

---

## ArrayList vs LinkedList -> bigO 시간은?
  
조회 삽입 삭제 갱신 :  

ArrayList 
삽입 삭제 : O(n) 
수정 : O(1)

LinkedList 모두 : O(1)


## Abstract vs Interface

Abstract : 객체 지향의 상속 받아서 추상 클래스를 구현해서 다형성을 만족 시킬 수 있게 사용 하는 것  
(다형성 : Overloading / overriding -> 상속 클래스마다 다르게 함수 내용을 바꿔서 실행할 수 있는 개념)  
Interface : 설계 명세 등을 필요할 때