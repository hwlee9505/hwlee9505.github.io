---
layout: default
title: 탑 level2
parent: Algorithm 스택/큐
nav_order: 6
---

# 탑 (자료구조 Stack)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

수평 직선에 탑 N대를 세웠습니다. 모든 탑의 꼭대기에는 신호를 송/수신하는 장치를 설치했습니다.  
발사한 신호는 신호를 보낸 탑보다 높은 탑에서만 수신합니다.  
또한, 한 번 수신된 신호는 다른 탑으로 송신되지 않습니다.  

예를 들어 높이가 6, 9, 5, 7, 4인 다섯 탑이 왼쪽으로 동시에 레이저 신호를 발사합니다.  
그러면, 탑은 다음과 같이 신호를 주고받습니다. 높이가 4인 다섯 번째 탑에서 발사한 신호는 높이가 7인 네 번째 탑이 수신하고, 높이가 7인 네 번째 탑의 신호는 높이가 9인 두 번째 탑이, 높이가 5인 세 번째 탑의 신호도 높이가 9인 두 번째 탑이 수신합니다. 높이가 9인 두 번째 탑과 높이가 6인 첫 번째 탑이 보낸 레이저 신호는 어떤 탑에서도 수신할 수 없습니다.


| 송신 탑(높이)   | 수신 탑(높이)        | 
|:-------------|:------------------|
| 5(4)         | 4(7)              |
| 4(7)         | 2(9)              |
| 3(5)         | 2(9)              |
| 2(9)         | -                 |
| 1(6)         | -                 |


맨 왼쪽부터 순서대로 탑의 높이를 담은 배열 heights가 매개변수로 주어질 때 각 탑이 쏜 신호를 어느 탑에서 받았는지 기록한 배열을 return 하도록 solution 함수를 작성해주세요.맨 왼쪽부터 순서대로 탑의 높이를 담은 배열 heights가 매개변수로 주어질 때 각 탑이 쏜 신호를 어느 탑에서 받았는지 기록한 배열을 return 하도록 solution 함수를 작성해주세요.


## 제한 조건

- heights는 길이 2 이상 100 이하인 정수 배열입니다.
- 모든 탑의 높이는 1 이상 100 이하입니다.
- 신호를 수신하는 탑이 없으면 0으로 표시합니다.


## 입출력 예

| heights          | return            | 
|:-----------------|:------------------|
| [6,9,5,7,4]      | [0,0,2,2,4]       |
| [3,9,9,3,5,7,2]  | [0,0,0,3,3,3,6]   |
| [1,5,3,6,7,6,5]  | [0,0,2,0,0,5,6]   |

## 입출력 예 설명

### 입출력 예 #1

앞서 설명한 예와 같습니다.

### 입출력 예 #2

[1,2,3] 번째 탑이 쏜 신호는 아무도 수신하지 않습니다.
[4,5,6] 번째 탑이 쏜 신호는 3번째 탑이 수신합니다.
[7] 번째 탑이 쏜 신호는 6번째 탑이 수신합니다.

### 입출력 예 #3

[1,2,4,5] 번째 탑이 쏜 신호는 아무도 수신하지 않습니다.
[3] 번째 탑이 쏜 신호는 2번째 탑이 수신합니다.
[6] 번째 탑이 쏜 신호는 5번째 탑이 수신합니다.
[7] 번째 탑이 쏜 신호는 6번째 탑이 수신합니다.

## 해결 전략

![](/assets/images/algorithm/top.jpeg)

## 해결 코드
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main
{
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        Stack<Integer> s = new Stack<>();
        Stack<Integer> index = new Stack<>();
        int n = Integer.parseInt(br.readLine());
        int[] arr = new int[n];
        StringTokenizer st = new StringTokenizer(br.readLine());
        arr[0] = 0;
        int high;
        for ( int i = 0 ; i < n; i ++)
        {
            high = Integer.parseInt(st.nextToken());
            while (!s.empty() && s.peek() < high)
            {
                s.pop();
                index.pop();
            }
            if (!s.empty())
                arr[i] = index.peek();
            s.push(high);
            index.push(i + 1);
        }

        for (int i = 0 ; i < n; i ++)
            System.out.println(arr[i]);
    }
}
```

## 해결 코드1
```java
import java.util.Stack;
class Solution {
    public int[] solution(int[] heights) {
         Stack<Integer> topS = new Stack<>();
        int[] answer = new int[heights.length];

        // 입력값으로 받는 배열을 topStack에 푸쉬 해줌
        for(int i : heights){
            topS.push(i);
        }
        // 스택이 비어있지 않을 때 까지
        while(!topS.isEmpty()){

            // 맨위의 것을 temp에 담아줌
            int temp = topS.pop();

            // 스택으로 빼주면서 가장 주변에 있는 자신보다 높은 타워를 answer[]에 삽입
            for(int i = topS.size(); i>=0; i--){
                if(temp < heights[i]){
                    answer[topS.size()] = i+1;
                    break;
                }
            }
        }
        return answer;
    }
}
```

## 해결 코드2
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int size = Integer.parseInt(br.readLine());

        int hegihts[] = new int[size];

        StringTokenizer st = new StringTokenizer(br.readLine()," ");

        int index = 0;
        while(st.hasMoreTokens()){
            hegihts[index++] = Integer.parseInt(st.nextToken());
        }

        for(int i : solution(hegihts)){
            System.out.print(i + " ");
        }
    }

    public static int[] solution(int[] height) {

        Stack<Tower> stack = new Stack<>();
        int[] answer = new int[height.length];

        for (int i = 0; i < height.length; i++) {
            Tower tower = new Tower(i + 1, height[i]);
            int receiveIdx = 0;


            // 스택이 비어있지 않다면
            while(!stack.isEmpty()){
                // 스택 상위의 것을 객체로 변환 시키고
                Tower top = stack.peek();
                // 그 변환시킨 객체의 높이와 새로 생성한 타워의 높이와 비교한다.
                if(top.height > tower.height){
                    receiveIdx = top.idx;
                    break;
                }
                stack.pop();
            }

            stack.push(tower);
            answer[i] = receiveIdx;

        }

        return answer;
    }
}

class Tower {

    int idx;
    int height;

    public Tower(int idx, int height) {
        this.idx = idx;
        this.height = height;
    }

    @Override
    public String toString() {
        return "idx : " + idx + " height : " + height;
    }
}
```
