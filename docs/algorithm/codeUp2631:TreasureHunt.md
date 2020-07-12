---
layout: default
title: CodeUp 2631
parent: Algorithm
nav_order: 18
---

# CodeUp 2628 보물 찾기
{: .no_toc }

---

## 문제 설명

수열 속에 숨어 있는 보물들을 찾아보자. n개의 자연수로 이루어진 수열이 있다.  
이 수열들 중 연속된 1개 이상의 원소들의 합이 정확히 k가 되면 이 구간은 보물구간이라고 한다.  
주어진 n개의 자연수 중에서 보물 구간이 몇 개 있는지 구하는 프로그램을 작성하시오.  

## 입력

첫 번째 줄에 자연수 n과 k가 공백으로 구분되어 입력된다.  
두 번째 줄에 n개의 각 원소가 공백으로 구분되어 입력된다.  

[입력값의 정의역]  
5<=n<=100,000  
각 원소는 1,000이하의 자연수  

## 출력

보물 구간의 수를 출력한다.  

## 입력 예시

5 15  
1 2 3 4 5 

## 출력 예시

1  

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
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         StringTokenizer st = new StringTokenizer(br.readLine(), " ");
# 
#         // n == 들어오는 갯수
#         int n = Integer.parseInt(st.nextToken());
# 
#         // 원소들의 합이 정확이 K가 되면 이 구간이 보물 구간!!
#         int k = Integer.parseInt(st.nextToken());
# 
#         String[] readLine = br.readLine().split(" ");
# 
#         int[] nums = new int[n];
# 
#         int idx = 0;
# 
#         for (String s : readLine) {
#             nums[idx++] = Integer.parseInt(s);
#         }
# 
#         int sum = 0;     // k와 비교를 할 sum 변수
#         int cursor = 0;  // 뒤에서 부터 줄려 나갈 인덱스
#         int count = 0;   // 결과를 도출해 내는 변수
# 
#         for (int i = 0; i < n; i++) {
# 
#             // 1. nums원소가 k보다 크다면 무시하기.
#             if (nums[i] > k) {
#                 continue;
#             }
#             // 2. nums원소가 k와 같다면
#             if (nums[i] == k) {
#                 count++;
#                 continue;
#             }
#             // 3. nums원소가 k보다 작다면
#             if (sum < k) {                // 합이 k보다 작을 경우
#                 sum += nums[i];
#             }
# 
#             if (sum > k) {                // 합이 k보다 크다면
#                 while (sum > k)           // *** 이것 때문에 고생 ***
#                     sum -= nums[cursor++];
#             }
# 
#             if (sum == k) {               // 합이 k와 같다면
#                 count++;
#                 sum -= nums[cursor++];
#             }
#         }
#         System.out.println(count);
#     }
# }
```