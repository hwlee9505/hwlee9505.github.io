---
layout: default
title: CodeUp 3129
parent: Algorithm
nav_order: 9
---

# CodeUp 3127 (자료구조 Stack 괄호 검사)
{: .no_toc }
[동빈나_중위표기법을 후위표기법으로 변환하기](http://blog.naver.com/PostView.nhn?blogId=ndb796&logNo=220654116881&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
---

## 문제 설명

괄호 문자열이 주어지면 올바른 괄호 문자열인지 판단하는 프로그램을 작성하시오.  
올바른 괄호 문자열이란 여는 괄호와 닫는 괄호의 짝이 맞고, 포함 관계에 문제가 없는 문자열을 말한다.  
예를 들어, )()( 인 경우 여는 괄호와 닫는 괄호의 짝이 맞지 않으므로 올바른 괄호 문자열이 아니다.  
(()())인 경우 괄호의 짝이 맞고 포함 관계가 맞으므로 올바른 괄호 문자열이다.  

## 입력

'('와 ')'로 이루어진 50,000글자 이하의 괄호 문자열이 입력된다.  
문자열 중간에 공백이나 다른 문자는 포함되지 않는다.  

## 출력

올바른 괄호 문자열이면 'good', 아니면 'bad'를 출력한다.  

## 입력 예시

))()((  

## 출력 예시

bad

## 도움말

stack을 이용하면 쉽게 판단할 수 있습니다.

## 해결 코드1
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.util.Stack;
# 
# public class Main {
# 
#     public static void main(String[] args) throws IOException {
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         String str = br.readLine();
# 
#         Stack<Character> stack = new Stack();
#         char[] gihos = str.toCharArray();
# 
#         System.out.println(Main.isRight(gihos, stack));
# 
#     }
# 
#     public static String isRight(char[] gihos, Stack<Character> stack) {
# 
#         for (char c : gihos) {
# 
#             if (c == '(') {
#                 stack.push(c);
#             } else {
#                 if (!stack.isEmpty()) {
#                     stack.pop();
#                 } else {    // 처음부터 ')'가 들어오는 경우를 대비
#                     return "bad";
#                 }
#             }
#         }
# 
#         if (stack.isEmpty()) {
#             return "good";
#         } else {
#             return "bad";
#         }
#     }
# }
```