---
layout: default
title: CodeUp 3102 
parent: Algorithm 스택/큐
nav_order: 7
---

# 기본 자료구조 문제
{: .no_toc }

---

## 문제 설명

피어나라 꿈나무들은 오늘 스택에 대해 공부할 것이다.  
STL stack 명령어를 익힐 수 있도록 해보자.  
N개의 명령어가 입력되면, 순서대로 동작하는 프로그램을 제작하시오.  

명령어 설명 :  

- push( x ) : x를 스택에 넣는다.(x는 정수) 괄호와 x사이에 공백이 반드시 존재한다.
- top() : 스택의 top 포인터가 가리키는 값을 출력한다.  만약 원소가 없다면 -1을 출력한다.
- pop() : 스택의 마지막에 들어온 원소를 삭제한다.
- size() : 스택안의 원소 개수를 출력한다.
- empty() : 스택이 비어있으면 true, 비어 있지 않으면 false 를 출력한다.


## 입력

첫째줄에 N이 입력된다.(1<=N<=200)  

둘째 줄 부터 각 줄에 하나씩 명령어 N개가 입력된다.  

## 출력


명령어에 따라 동작결과를 순서대로 출력한다.  
push와 pop은 출력되는 결과가 없음에 유의한다.  

### 입력 예시

7  
push( 5 )  
top()  
push( 7 )  
push( 3 )  
top()  
pop()  
size()  

### 출력 예시

5
3
2

## 해결 코드1
```yaml
# import java.io.BufferedReader;
# import java.io.InputStreamReader;
# import java.io.IOException;
# import java.util.Stack;
# 
# public class Main{
# 
#     public static void main (String[] args) throws IOException{
# 
#         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#         Stack<String> stack = new Stack();
# 
#         int size = Integer.parseInt(br.readLine());
#         String[] strArr = new String[size];
# 
#         // 먼저 br.readLine()은 따로 받아놓고 하기
#         for(int i =0; i< size; i++){
#             strArr[i] = br.readLine();
#         }
# 
#         for(String command : strArr){
#             if(command.contains("push")) {
#                 String[] nums = command.split(" +");
#                 stack.push(nums[1]);
#             }else if(!stack.isEmpty() && command.equals("top()")) {
#                 System.out.println(stack.peek());
#             }else if(stack.isEmpty() && command.equals("top()")) {  // java api stack의 peek()는 비어있으면 -1을 반환하지 않고
#                 System.out.println("-1");                           // Throws: EmptyStackException - if this stack is empty.
#             }else if(!stack.isEmpty() && command.equals("pop()")){
#                 stack.pop();
#             }else if(command.equals("size()")){
#                 System.out.println(stack.size());
#             }else if(command.equals("empty()")){
#                 System.out.println(stack.isEmpty());
#             }
#         }
#     }
# }
```