---
layout: default
title: CodeUp 3021
parent: Algorithm
nav_order: 6
---

# CodeUp 3021 (큰 수 처리)
{: .no_toc }

---

## 문제 설명

int는 32비트, long long 은 64비트라서 이 보다 더 큰 숫자는 저장할 수 없다.  
아주 큰 숫자의 덧셈을 하려고 한다.  
계산 결과를 출력하시오.  

## 입력

첫째줄과 둘째줄에 큰 수 a, b가 입력된다. (a, b는 100자리 이하의 정수)  

## 출력

큰 수 덧셈의 결과를 출력한다.  

### 입력 예시

12345678910111213  
2839287  

### 출력 예시

12345678912950500  

## 해결 코드1
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.math.BigInteger;
# /* 
#   byte형의 범위  : -128 ~ 127
#   short형의 범위 : -32768 ~ 32767
#   int형의 범위   : -2147483648 ~ 2147483647
#   long형의 범위  : -9223372036854775808 ~ 9223372036854775807
# 
#   long형의 범위가 넘어가는 정수일 경우에
#   java.math.BigInteger을 사용한다.
#   여기서 사칙연산은 .add .subtract .mutiply .divide을 사용하도록 한다.
# */
# 
#     public static void main(String[] args) throws IOException {
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
# 
#         BigInteger str1 = new BigInteger(br.readLine());
#         BigInteger str2 = new BigInteger(br.readLine());
# 
#         System.out.println(str1.add(str2));
# 
#     }
# }
```