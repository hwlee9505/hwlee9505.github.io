---
layout: default
title: Operating System
parent: CS 지식
nav_order: 11
---

# Operating System
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

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
