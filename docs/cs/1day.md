---
layout: default
title: Week 1
parent: CS 지식
nav_order: 1
---

# SW 작무 면접 스터디 1주차
{: .no_toc }

---

## Table of contents
{: .no_toc .text-delta }

## 자료구조에서 set과 list의 차이는?

set : 순서 없음, 중복 데이터 불가(집합 성격)  
list : 순서 있음(index 사용 가능), 중복 허용  


## context-switching이란?

문맥 교환(context switch)이란 하나의 프로세스가 CPU를 사용 중인 상태에서 다른 프로세스가 CPU를 사용하도록 하기 위해, 이전의 프로세스의 상태(문맥)를 보관하고 새로운 프로세스의 상태를 적재하는 작업을 말한다.  
한 프로세스의 문맥은 그 프로세스의 프로세스 제어 블록(PCB)에 기록되어 있다.  
(위키피디아)

## thread와 process중 어느것이 비용이 작은가?

프로세스는 독립된 메모리 공간을 가지지만, 스레드는 한 프로세스 내에서 메모리를 공 유하므로 비용이 더 작다.

## 다대다 테이블의 관계를 스키마로 어떻게 작성할래?

매핑 테이블을 사용한다

## 리팩토링이란?

리팩터링(refactoring)은 소프트웨어 공학에서 '결과의 변경 없이 코드의 구조를 재조정함'을 뜻한다.  
주로 가독성을 높이고 유지보수를 편하게 한다.  
버그를 없애거나 새로운 기능을 추가하는 행 위는 아니다.  
사용자가 보는 외부 화면은 그대로 두면서 내부 논리나 구조를 바꾸고 개선하는 유지보수 행 위이다.  
(위키피디아)

## http와 https의 차이점?
HTTPS(HyperText Transfer Protocol over Secure Socket Layer, HTTP over  
TLS,[1][2] HTTP over SSL,[3] HTTP Secure[4][5])는  
월드 와이드 웹 통신 프로토콜인 HTTP의 보안이 강화된 버전이다.  
HTTPS는 소켓 통신에서 일반 텍스트를 이용하는 대신에, SSL이나 TLS 프로토콜을 통해 세 션 데이터를 암호화한다.  
따라서 데이터의 적절한 보호를 보장한다.  
HTTPS의 기본 TCP/IP 포트는 443이다.  
HTTPS를 사용하는 웹페이지의 URI는 'http://'대신 'https://'로 시작한다.  
(위키피디아)