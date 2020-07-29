---
layout: default
title: Week 4
parent: CS 지식
nav_order: 4
---

# 4주차 (데이터베이스 & 자바 & 스프링) 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

# 병준님 -> 성용
{: .label .label-red }

## database의 index란?

테이블에 대한 동작의 속도를 높여주는 자료구조.  

[관련 링크](https://ko.wikipedia.org/wiki/%EC%9D%B8%EB%8D%B1%EC%8A%A4_(%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4)){: .btn .fs-5 .mb-4 .mb-md-0 }  

---

## 정규화가 무엇인지와 하는 이유는?  

정규화 : 관계형 데이터베이스의 설계에서 중복을 최소화하게 데이터를 구조화하는 프로세스  
목적 :  
1. 데이터베이스의 변경(갱신, 상십, 삭제)시 이상 현상 제거  
  - 삽입 이상 : 어떤 특정 사실은 전혀 기록되지 않는 경우(null 발생)  
  - 갱신 이상 : 일부는 변경되고 일부는 변경되지 않는 모순 상태가 발생할 수 있다.  
  - 삭제 이상 : 데이터의 삭제가 전혀 다른 사실에 대한 데이터의 삭제도 필요로 하는 경우  
2. DB 구조 확장시 재 디자인 최소화  
3. 사용자의 데이터 모델을 더욱 의미있게 : 현실세계의 개념과 관계를 반영  
4. 다양한 질의 지원  

[관련 링크](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EC%A0%95%EA%B7%9C%ED%99%94){: .btn .fs-5 .mb-4 .mb-md-0 }  

---

## Commit과 Rollback이란?  

Commit : 트랜잭션에 대한 작업이 성공적으로 끝났을 때, 이 트랜잭션이 행한 갱신 연산이 완료된 것을 트랜잭션 관리자에게 알려주는 연산  
Rollback : 트랜잭션 처리가 비정상적으로 종료되었을 때, 모든 연산을 취소시키는 연산  

[관련 링크](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Interview/Interview%20List.md#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4){: .btn .fs-5 .mb-4 .mb-md-0 }  

---

## 상속과 합성이 무엇인지, 그리고 차이는?  

상속 : is-a 관계(extends). 캡슐화 약화됨. 실행 시점에 코드가 유연하지 못함  
합성 : has-a 관계(field)  

[관련 링크](https://biggwang.github.io/2019/07/31/OOP/%EC%83%81%EC%86%8D%EB%B3%B4%EB%8B%A4%EB%8A%94%20%ED%95%A9%EC%84%B1%EC%9D%84%20%EC%82%AC%EC%9A%A9%ED%95%B4%EC%95%BC%20%ED%95%98%EB%8A%94%20%EC%9D%B4%EC%9C%A0/){: .btn .fs-5 .mb-4 .mb-md-0 }  

---

## int 자료형에 Integer.MAX_VALUE에 1을 더하면?  

자바는 기초자료형에 대해 overflow를 따로 검출하지 않는다. 따라서 음수 중 가장 작은 값인 -Integer.MAX_VALUE - 1이 될 것이다.  

![](/assets/images/cs/week4.png)  

추가설명 : Integer.MAX_VALUE을 2의 보수로 나타내면  
01111111111111111....1111(32자리) 이다. 여기에 overflow가 나면  
10000000000000000....0000(32자리)가 되고, 이 값은 음수의 가장 작은 값이다.  

## sping의 의존성 주입이란?  
한 객체가 다른 객체를 참조하고 있는 것을 의존성을 가진다고 하는데, 이러한 의존성을 직접 관리하지 않고 framework에 위임하는 것을 말한다. 직접 의존성을 관리하면  
1) 긴밀한 결합(tight coupling)이 발생  
2) 하나의 모듈 변경에 따른 다른 모듈의 변경 수반  
3) unit test 어려워짐  
이라는 단점이 존재함. 

DI(Dependency Injection, 의존성 주입)는 IoC(Inversion Of Control, 제어의 역전)라고도 불림. IoC는 다음과 같은 특징을 가짐  
1) 개발자가 모든 것을 제어하지만, 코드 전체에 대한 제어는 framework가 함  
2) 개발자가 설정하면 container가 알아서 처리  

즉, 개발자는 framework 속에서 프로그래밍을 하는 것. DI를 통해 다음과 같은 이점을 얻을 수 있다.  
1) 중복성 감소  
2) 재사용성 증가  
3) 더 많은 테스트 코드 생성 가능  
4) 코드 읽기가 더 쉬워짐  

[관련 링크](https://gmlwjd9405.github.io/2018/11/09/dependency-injection.html){: .btn .fs-5 .mb-4 .mb-md-0 }  

