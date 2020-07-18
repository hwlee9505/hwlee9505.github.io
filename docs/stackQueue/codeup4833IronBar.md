---
layout: default
title: 쇠막대기 leve2
parent: Algorithm 스택/큐
nav_order: 8
---

# 쇠막대기 (Stack), CodeUp4833
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

## 문제 설명

여러 개의 쇠막대기를 레이저로 절단하려고 한다. 효율적인 작업을 위해서 쇠막대기를 아래에서 위 로 겹쳐 놓고, 레이저를 위에서 수직으로 발사하 여 쇠막대기들을 자른다. 쇠막대기와 레이저의 배 치는 다음 조건을 만족한다.  
- 쇠막대기는 자신보다 긴 쇠막대기 위에만 놓일 수 있다.  
- 쇠막대기를 다른 쇠막대기 위에 놓는 경우 완 전히 포함되도록 놓되, 끝점은 겹치지 않도록 놓는다.  
- 각 쇠막대기를 자르는 레이저는 적어도 하나 존재한다.  
- 레이저는 어떤 쇠막대기의 양 끝점과도 겹치지 않는다.  
아래 그림은 위 조건을 만족하는 예를 보여준다. 수평으로 그려진 굵은 실선은 쇠막대기이고, 점은 레이저의 위치, 수직으로 그려진 점선 화살표는 레이저의 발사 방향이다.  

![](/assets/images/algorithm/ironBar.png)

이러한 레이저와 쇠막대기의 배치는 다음과 같이 괄호를 이용하여 왼쪽부터 순서대로 표현할 수 있다.  
(a) 레이저는 여는 괄호와 닫는 괄호의 인접한 쌍 '()' 으로 표현된다. 또한, 모든 '()'는 반드 시 레이저를 표현한다.  
(b) 쇠막대기의 왼쪽 끝은 여는 괄호 '(' 로, 오 른쪽 끝은 닫힌 괄호 ')' 로 표현된다.  
위 예의 괄호 표현은 그림 위에 주어져 있다.  
쇠막대기는 레이저에 의해 몇 개의 조각으로 잘려 지는데, 위 예에서 가장 위에 있는 두 개의 쇠막 대기는 각각 3개와 2개의 조각으로 잘려지고, 이 와 같은 방식으로 주어진 쇠막대기들은 총 17개 의 조각으로 잘려진다.  
쇠막대기와 레이저의 배치를 나타내는 괄호 표현 이 주어졌을 때, 잘려진 쇠막대기 조각의 총 개수 를 구하는 프로그램을 작성하시오.  

## 입력

한 줄에 쇠 막대기와 레이저의 배치를 나타내는 괄호 표현이 공백 없이 주어진다. 괄호 문자의 개수는 최대 100,000이다.  

## 출력

잘려진 조 각의 총 개수를 나타내는 정수를 한 줄에 출력한다.

## 입력 예시

()(((()())(())()))(())

## 출력 예시

17

## 해결 코드
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.Stack;

public class Main{

    public static void main (String[] args) throws IOException{

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String s = br.readLine();
        Stack<Integer> stack = new Stack<>();
        int count = 0;

        for(int i = 0 ; i < s.length(); i++){

            if(String.valueOf(s.charAt(i)).equals("(")){    // 1) "("이 들어온다면 == 쇠막대기 시작점
                stack.push(i);                              // ㄴ index i를 push

            }else{                                          // 2) ")"이 들어온다면
                if(stack.peek() == i-1){                    // 2-1)** 바로 전것이 전 인덱스인가?
                    stack.pop();                            // 레이저다 pop;
                    count += stack.size();                  // 현재 스택의 사이즈를 count에 더하기 (한줄 쭉 짤려나간거?)
                }else{                                      // 2-2) 레이저가 아니다. == 쇠막대기 끝점
                    stack.pop();                            // stack pop;
                    count++;                                // count 터 1을 늘림 (어렵다)
                }
            }
        }
        System.out.println(count);
    }
}
```