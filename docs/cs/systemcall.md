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



## 시작하기에 앞서

리눅스 kernel을 수정하여 Stack 1) push와 2) pop System Call을 추가하고, 응용프로그램의 호출에 의해 동작을 확인해보는 시간을 갖도록 하겠습니다.  

---

## 커널에서 수정해야 할 주요 파일목록

1. (linux)/arch/x86/entry/syscalls/syscall_64.tbl (64비트 머신)
- 시스템 콜 tbl에 push와 pop의 고유번호를 지정해주자
2. (linux)/include/linux/syscalls.h
- push와 pop의 함수원형(=함수선언부)을 선언해주자
3. (linux)/my_stack_syscall.c 
- push와 pop을 구현해보자
4. (linux)/Makefile 
- 커널 컴파일 시 구현한 push와 pop이 컴파일이 되도록 Makefile을 수정해주자

```markdown
(linux)는 커널의 소스코드가 저장된 루트 폴더입니다.  
저의 경우는 /usr/src/linux-5.2.10 입니다.
```

---

## syscall_64.tbl

![](/assets/images/cs/systemcall/syscall1.png)  

(linux)/arch/x86/entry/syscalls로 이동합니다.  

syscalls라는 디렉토리에 `시스템 콜 함수들의 이름에 대한 심볼정보를 모아놓은 파일`이 있는데 그것이 바로 `syscall_64.tbl`파일 입니다.  

이제 syscall_64.tbl에 `시스템 콜 push와 pop의 number(고유번호)를 저장` 하기위해 코드를 추가 할 것입니다.  

335  common  hwlee_push  _x64_sys_hwlee_push  
336  common  hwlee_pop   _x64_sys_hwlee_pop  

![](/assets/images/cs/systemcall/syscall_64tbl.png)  

```markdown
저는 syscall_64.tbl파일안의 내용을 gedit라는 에디터로 push와 pop의 고유번호 335와 336를 추가하였습니다.  
```

---

## 2. syscalls.h  

![](/assets/images/cs/systemcall/syscall2.png)  

(linux)/include/linux로 이동합니다.  

linux 디렉토리에 시스템 콜 함수들의 전체적인 기능을 간략한 형태로 정의한 파일 이 있는데 그것이 바로 syscalls.h 파일 입니다.  

이제 syscalls.h 가장 마지막 부분에 함수 원형을 등록 해주겠습니다.  
asmlinkage  void  sys_hwlee_push(int);  
asmlinkage  int  sys_hwlee_pop(void);  

```markdown
asmlinkage를 사용하는 이유  
시스템 콜 호출은 assembly 코드로 작성되어있는 int 80인터럽트 핸들러에서 호출됩니다.  
asmkinkage를 함수 앞에 선언하면, assembyly code에서도 C함수 호출이 가능해집니다.  
```

![](/assets/images/cs/systemcall/syscalls_h.png)  

---



