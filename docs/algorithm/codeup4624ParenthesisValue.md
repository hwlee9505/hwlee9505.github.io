---
layout: default
title: CodeUp 4624
parent: Algorithm
nav_order: 12
---

# CodeUp 4624 괄호의 값 (자료구조 Stack)
{: .no_toc }

---

## 문제 설명

4개의 기호 '(', ')', '[', ']'를 이용해서 만들어지는 괄호열 중에서 올바른 괄호열이란 다음과 같이 정의된다.  
(1) 한 쌍의 괄호로만 이루어진 '()'와 '[]'는 올바른 괄호열이다.  
(2) 만일 X가 올바른 괄호열이면 '(X)'이나 '[X]'도 모두 올바른 괄호열이 된다.  
(3) X와 Y 모두 올바른 괄호열이라면 이들을 결합한 XY도 올바른 괄호열이 된다.  

예를 들어 '(()[[]])'나 '(())[][]' 는 올바른 괄호열이지만 '([)]' 나 '(()()[]' 은 모두 올바른 괄호열이 아니다.  
우리는 어떤 올바른 괄호열 X에 대하여 그 괄호열의 값(괄호값)을 아래와 같이 정의하고 값(X)로 표시한다.  
(1) '()' 인 괄호열의 값은 2이다.  
(2) '[]' 인 괄호열의 값은 3이다.  
(3) '(X)' 의 괄호값은 2×값(X) 으로 계산된다.  
(4) '[X]' 의 괄호값은 3×값(X) 으로 계산된다.  
(5) 올바른 괄호열 X와 Y가 결합된 XY의 괄호값은 값(XY) = 값(X)+값(Y) 로 계산된다.  

예를 들어 '(()[[]])([])' 의 괄호값을 구해보자. '()[[]]' 의 괄호값이 2+3×3=11 이므로 '(()[[ ]])'의 괄호값은 2×11=22 이다. 그리고 '([])'의 값은 2×3=6 이므로 전체 괄호열의 값은 22+6 = 28 이다.  
여러분이 풀어야 할 문제는 주어진 괄호열을 읽고 그 괄호값을 앞에서 정의한대로 계산하여 출력하는 것이다.  

## 입력

첫 째 줄에 괄호열을 나타내는 문자열(스트링)이 주어진다. 단 그 길이는 1 이상, 30 이하이다.  

## 출력

첫째 줄에 그 괄호열의 값을 나타내는 정수를 출력한다. 만일 입력이 올바르지 못한 괄호열이면 반드시 0을 출력해야 한다.  

## 입력 예시

(()[[]])([])

## 출력 예시

28

## 해결 코드 X (처음에 생각했던 코드)

아직 알고리즘 초보이다 보니
1. 처음에 괄호들을 중위표기법으로 표현한 후
2. 중위표기 -> 후위표기법 으로 변환한 뒤
3. 후위표기법을 이용하여 계산하려 했으나 
시간을 허투루 소비하는 것 같아 다른 소스를 보았는데 역시나 내 접근방법 자체가 별로였던 같다.
아직도 요령이 부족한듯 하다;;


```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.util.Stack;
# 
# public class Main {
# 
#     static Stack<Character> charStack = new Stack<>();
#     static StringBuffer paren = new StringBuffer();
# 
#     public static void main(String[] args) throws IOException {
# 
#         Stack<Integer> stack = new Stack();
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         String str = br.readLine();
# 
#         for (int i = 0; i < str.length(); i++) {
# 
#             char temp = str.charAt(i);
# 
#             if (temp == '(' || temp == '[') {
#                 stack.push(i);
#             } else {
#                 // +인 경우에
#                 if (stack.peek() == (i - 1)) {
#                     if (temp == ')') {
#                         stack.pop();
#                         paren.append('+');
#                         paren.append('2');
# 
#                     } else if (temp == ']') {
#                         stack.pop();
#                         paren.append('+');
#                         paren.append('3');
#                     }
#                 }
#                 // *인 경우에
#                 else {
#                     if (temp == ')') {
#                         stack.pop();
#                         paren.append('*');
#                         paren.append('2');
#                     } else if (temp == ']') {
#                         stack.pop();
#                         paren.append('*');
#                         paren.append('3');
#                     }
#                 }
#             }
#         }
# 
#         System.out.println("중위순회 = " + paren);
# 
#         //////////////////////////////////////////////////////////
#         //      2.    먼저 중위 표기법 -> 후위 표기법으로 고치기          //
#         /////////////////////////////////////////////////////////
# 
#         char[] inputs = paren.toString().substring(1, paren.length()).toCharArray();
# 
# 
#         paren.setLength(0); //  paren 초기화 , for 재사용을 위해서
# 
#         // stack도 재사용하려 했지만 제너릭스가 달라 새로 static 스택을 만듬
# 
#         for (char c : inputs) {
# 
#             switch (c) {
# 
#                 case '+':
#                     gotOper(c, 1);
#                     break;
#                 case '*':
#                     gotOper(c, 2);
#                     break;
#                 default:
#                     paren.append(c);
#                     break;
#             }
#         }
#         while (!charStack.isEmpty()) {
#             char temp = charStack.pop();
#             paren.append(temp);
#         }
#         System.out.println("중위 -> 후위 = " + paren);
# 
#         //////////////////////////////////////////////////////////
#         //      3.LAST       후위 순회를 이용해서 수식 계산하기          //
#         /////////////////////////////////////////////////////////
# 
#         for (int i = 0; i < paren.length(); i++) {
# 
#             char temp = paren.toString().charAt(i);
# 
#             if (temp != '+' && temp != '*') {
#                 stack.push(temp - '0');           // 처음에 썻던 스택을 재사용!
#                 continue;
#             }
# 
#             int second = stack.pop();
#             int first = stack.pop();
# 
#             if (temp == '+') {
#                 stack.push(first + second);
#             } else if (temp == '*') {
#                 stack.push(first * second);
#             }
#         }
# 
#         System.out.println("result = " + stack.pop());
# 
#     }
# 
#     private static void gotOper(char opThis, int prec1) {
# 
#         while (!charStack.isEmpty()) {
#             char onTop = charStack.pop();
#             int prec2;
#             if (onTop == '+') {
#                 prec2 = 1;
#             } else {
#                 prec2 = 2;
#             }
#             if (prec2 < prec1) {
#                 charStack.push(onTop);
#                 break;
#             } else {
#                 paren.append(onTop);
#             }
#         }
#         charStack.push(opThis);
#     }
# }
```

## 해결 코드2

[팡스블로그 스택-괄호의 값](https://pangsblog.tistory.com/53){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
