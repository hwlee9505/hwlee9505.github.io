---
layout: default
title: 주식가격 level2
parent: Algorithm 스택/큐
nav_order: 10
---

# 주식가격 (자료구조 Queue)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

## 문제 설명

초 단위로 기록된 주식가격이 담긴 배열 prices가 매개변수로 주어질 때, 가격이 떨어지지 않은 기간은 몇 초인지를 return 하도록 solution 함수를 완성하세요.  

## 제한 사항

* prices의 각 가격은 1 이상 10,000 이하인 자연수입니다.  
* prices의 길이는 2 이상 100,000 이하입니다.                                              인쇄 작업의 중요도는 1~9로 표현하며 숫자가 클수록 중요하다는 뜻입니다.
                                                                                       location은 0 이상 (현재 대기목록에 있는 작업 수 - 1) 이하의 값을 가지며 대기목록의 가장 앞에 있으면 0, 두 번째에 있으면 1로 표현합니다.

## 입출력 예

| prices           | return           | 
|:-----------------|:-----------------|
| [1, 2, 3, 2, 3]  | [4, 3, 1, 1, 0]  |

## 입출력 예 설명

* 1초 시점의 ₩1은 끝까지 가격이 떨어지지 않았습니다.  
* 2초 시점의 ₩2은 끝까지 가격이 떨어지지 않았습니다.  
* 3초 시점의 ₩3은 1초뒤에 가격이 떨어집니다. 따라서 1초간 가격이 떨어지지 않은 것으로 봅니다.  
* 4초 시점의 ₩2은 1초간 가격이 떨어지지 않았습니다.  
* 5초 시점의 ₩3은 0초간 가격이 떨어지지 않았습니다.  

## 해결 코드
```java
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;

public class Main {

    public static void main(String[] args) {
        System.out.println(Arrays.toString(Main.solution(new int[]{1, 2, 3, 2, 3})));
    }


    public static int[] solution(int[] prices) {
        int[] answer = new int[prices.length];

        Queue<Integer> queue = new LinkedList<>();
        Stack<Integer> resultStack = new Stack<>();     //  새로 넣은 push한 것을
                                                        //  조건문에 따라
                                                        //  자주 업데이트 해야하는 상황이 오기 때문에 Stack을 사용!

        for (int p : prices) {
            queue.offer(p);
        }

        int idx = 0;
        while (!queue.isEmpty()) {

            idx ++;
            int temp = queue.poll();

            if (queue.size() == 0) {
                resultStack.push(0);
                break;
            } else {
                resultStack.push(queue.size());
            }

            for (int i = prices.length - queue.size(); i < prices.length; i++) {

                if (temp > prices[i]) {
                    resultStack.pop();
                    resultStack.push(i-idx+1);
                    break;
                }
            }
        }

        // resultStack에 거꾸로 담겨있는 결과 값을 answer[]에 담아준다.
        int answerIdx = answer.length-1;
        while(!resultStack.isEmpty()){
            answer[answerIdx--] = resultStack.pop();
        }

        return answer;
    }
}
```