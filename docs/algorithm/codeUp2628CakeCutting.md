---
layout: default
title: CodeUp 2628 x
parent: Algorithm
nav_order: 16
---

# CodeUp 2628 케익 자르기 X 완벽이해 X
{: .no_toc }

---

## 문제 설명

왼쪽 같이 둥근 케잌을 2번의 칼질로 케잌을 나누려고 한다.  
오른쪽 그림과 같이 케익의 둘레에 시계방향으로 1 100까지 일정한 간격으로 번호가 부여되어 있다.  


![](/assets/images/algorithm/cakeCutting1.png)

칼로 자르려고 하는 부분은 2개의 정수로 표현한다.  
이 2번의 칼질로 4조각의 케잌을 만들려면 반드시 교차하는 부분이 생긴다.  
  
칼로 자르려는 부분이 두 군데 주어질 때 칼로 잘리는 부분이 4조각이 되는지 판단하는 프로그램을 작성하시오.  
 
즉, 교차하는지 유무를 판단하시오. 아래 예는 12 53과 99 45를 자른 예를 나타낸다.  

![](/assets/images/algorithm/cakeCuttin2.png)


## 입력

첫 번째 줄에는 첫 번째 현의 정보를 나타내는 두 정수 a,b가  
두 번째 줄에는 두 번째 현의 정보를 나타내는 두 정수 c,d가 입력된다.  
(1<=a,b,c,d<=100:a,b,c,d는 모두 다르다.)  

## 출력

주어진 두 잘린 부분이 교차한다면 "cross", 교차하지 않는다면 "not cross"를 출력한다.  

### 입력 예시

12 53  
99 45  

### 출력 예시

3cross

## 해결 코드
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.util.StringTokenizer;
# 
# public class Main {
# 
#     /*
#         기하 문제이다.
#      */
# 
#     public static void main(String[] args) throws IOException {
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
# 
#         StringTokenizer st = new StringTokenizer(br.readLine(), " ");
#         int a = Integer.parseInt(st.nextToken());
#         int b = Integer.parseInt(st.nextToken());
#         st = new StringTokenizer(br.readLine(), " ");
#         int c = Integer.parseInt(st.nextToken());
#         int d = Integer.parseInt(st.nextToken());
# 
#         if (a < b) {    //  a가 b보다 크게 하기
#             int temp = a;
#             a = b;
#             b = temp;
#         }
# 
#         int k = 0; // k : a와 b 사이에 있는 점의 개수
# 
#         if (a < c || c < b) {
#             k++;
#         }
# 
#         if (a < d || d < b) {
#             k++;
#         }
# 
#         if (k == 1) {
#             System.out.println("Cross");
#         } else {
#             System.out.println("Not Cross");
#         }
#     }
# }
```