---
layout: default
title: CodeUp 2625
parent: Algorithm
nav_order: 15
---

# CodeUp 2625 삼각화단 만들기 (Small)
{: .no_toc }

---

## 문제 설명

주어진 화단 둘레의 길이를 이용하여 삼각형 모양의 화단을 만들려고 한다. 이 때 만들어진 삼각형 화단 둘레의 길이는 반드시 주어진 화단 둘레의 길이와 같아야 한다. 또한, 화단 둘레의 길이와 각 변의 길이는 자연수이다.  
예를 들어, 만들고자 하는 화단 둘레의 길이가 9m라고 하면  

한 변의 길이가 1m, 두 변의 길이가 4m인 화단,  
한 변의 길이가 2m, 다른 변의 길이가 3m, 나머지 변의 길이가 4m인 화단,  
세 변의 길이가 모두 3m인 3가지 경우의 화단을 만들 수 있다.  

![](/assets/images/algorithm/makeTriangle.png)

둘레의 길이를 입력받아서 만들 수 있는 서로 다른 화단의 수를 구하는 프로그램을 작성하시오.  
 

## 입력

화단의 길이 이 주어진다.(단, 3 <= n <= 100)

## 출력

n으로 만들 수 있는 서로 다른 화단의 수를 출력한다.

### 입력 예시

9

### 출력 예시

3

## 해결 코드
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# 
# public class Main {
# 
#     public static void main(String[] args) throws IOException {
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         int num = Integer.parseInt(br.readLine());
# 
#         int cnt = 0;
#         for (int a = 1; a < num; a++) {
#             for (int b = 1; b < num; b++) {
#                 for (int c = 1; c < num; c++) {
#                     if(a <= b && b<=c && a+b>c && a+b+c == num){    // 가장 큰 변 < 나머지 두변의 합
#                         cnt ++;
#                     }
#                 }
#             }
#         }
#         System.out.println(cnt);
#     }
# }
```