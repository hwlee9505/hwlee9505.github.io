---
layout: default
title: CodeUp 3127
parent: Algorithm 스택/큐
nav_order: 2
---

# Stack 후위 표기식의 계산
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

우리가 일상 생활에서 사용하는 수학식은 대부분 중위 표기법이다.  
중위 표기법은 어떠한 이항 연산에 대해 연산 대상 사이에 연산자를 표기하는 방식이다.  

예를 들면  
3+5∗7  
(6+9)∗8  
등이 있다. 
 
하지만 이런 중위 표기법은 연산자 우선 순위에 따라 괄호를 해야 한다는 단점이 있다.  
이에 반해 후위 표기법은 두 피연산자를 먼저 쓰고 그 뒤에 연산자를 표기하는 방식이다.  
위의 중위 표현을 

예로 들면  
3 5 7 * +  
6 9 + 8 *  
이다.  

후위 표기법은 연산자의 순서가 곧 계산 순서이므로 괄호가 필요 없다는 장점이 있다.  
후위 표기법으로 된 식을 입력 받아 계산 결과를 출력하는 프로그램을 작성하시오.  

## 입력

후위 표기법으로 된 식이 입력된다.  
주어지는 식은 자연수와 덧셈, 뺄셈, 곱셈만으로 이루어져 있으며, 각 자연수와 연산자 사이는 띄어 쓰기 되어 있다.  
전체 식의 길이는 공백 문자 포함 200자 이하이다.  
식에 포함된 자연수 및 식의 계산 결과는 2^30을 넘지 않는다.  

## 출력

식의 계산결과를 출력한다.  

## 입력 예시

1 2 3 * + 4 5 - 6 * + 

## 출력 예시

1

## 도움말

  1 2 3 * + 4 5 - 6 * +  
= 1 + 2 * 3 + (4 - 5) * 6  
= 1  

## 해결 코드
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        Stack<Integer> stack = new Stack<>();

        // StringTokenizer  
        // split 사용할 필요 없이 구분 짓기 위한 클래스
        StringTokenizer st = new StringTokenizer(br.readLine(), " ");

        // 후위 표기식 계산 알고리즘
        while (st.hasMoreTokens()) {

            String temp = st.nextToken();

            // 1) 항목이 피연산자 이면
            // push(item)
            if (!"+".equals(temp) && !"-".equals(temp) && !"*".equals(temp)) {
                stack.push(Integer.parseInt(temp));
                continue;
            }

            // 2) 항목이 연산자 이면
            // second = pop();
            // first = pop();
            // push(result);
            int second = stack.pop();
            int first = stack.pop();

            if ("+".equals(temp)) {
                stack.push(first + second);
            } else if ("-".equals(temp)) {
                stack.push(first - second);
            } else if ("*".equals(temp)) {
                stack.push(first * second);
            }
        }

        // 3) 마지막으로
        // final_result = pop(s);
        System.out.println(stack.pop());
    }
}
```