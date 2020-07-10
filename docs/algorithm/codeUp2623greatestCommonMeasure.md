---
layout: default
title: CodeUp 2623
parent: Algorithm
nav_order: 14
---

# CodeUp 2623 최대공약수
{: .no_toc }

---

## 문제 설명

두 정수 a,b를 입력받아서,a,b의 최대공약수를 출력하시오.

## 입력

정수 a,b가 공백으로 구분되어 입력된다.(1<=a,b<=10,000)

## 출력

a,b의 최대공약수를 출력한다.

### 입력 예시

64 128

### 출력 예시

64

## 해결 코드
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.util.StringTokenizer;
# 
# public class Main {
# 
#     public static void main(String[] args) throws IOException {
# 
#         // 유클리드 호제 법으로 최대공약수 구하는 방식
# 
#         // 여기서 기억할 공식은 큰 수 A를 작은수 B로 나누었을때 나누어 떨어진다면 최대공약수는 B가 된다.
# 
#         // 1)  입력 받은 두 수중 큰 수를 A, 작은수를 B로 정한다.
#         // 2)  A 를 B 로 나눈값의 나머지를 R로 지칭한다.
#         // 3)  R 이 0이라면 A는 B로 나누어 지기 때문에 최대 공약수는 B가 된다.
#         // 4)  만약 R이 0이 아니라면 A값은 B로, B 값은 R로 변경한뒤 3번 과정을 반복한다.
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         StringTokenizer st = new StringTokenizer(br.readLine(), " ");
# 
#         int x = Integer.parseInt(st.nextToken());
#         int y = Integer.parseInt(st.nextToken());
# 
#         int max = Math.max(x, y);
#         int min = Math.min(x, y);
# 
#         while (min > 0) {
#             int tmp = max;
#             max = min;
#             min = tmp % min;
#         }
# 
#         System.out.println(max);
#     }
# }
```