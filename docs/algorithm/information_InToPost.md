---
layout: default
title: Stack 중위표기법->후위표기법
parent: Algorithm
nav_order: 11
---

# Info 스택 중위표기법 -> 후위표기법
{: .no_toc }

---

## 설명

일반적으로 우리 인간은 중위연산식을 사용합니다.  
중위연산식이란 연산자가 피연산자 사이에 있는 식을 말합니다.  
하지만 단점은 연산자의 우선순위에 의해서 계산순서가 바뀌기 때문에 컴퓨터로 처리하기에는 적합하지 않습니다.
컴퓨터로는 후위 연산식을 사용할 때 연산자의 우선순위에 관계없이 순서대로 계산할 수 있기 때문에 더욱 편리할 수 있습니다.


[w3big.com 자바 예 - 후위 표기로 중위 식을 변환하는 스택을 사용](http://www.w3big.com/ko/java/data-intopost.html){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }


## 해결 코드
```yaml
# import java.io.IOException;
# 
# public class InToPost {
# 
# 
#     // Vector로 구현된 Stack 라이브러리를 쓰지않고
#     // 직접 정적 배열을 이용한 내부 클래스를 사용.
#     class Stack {
# 
#         private int maxSize;
#         private char[] stackArray;
#         private int top;
# 
#         public Stack(int max) {
#             maxSize = max;
#             stackArray = new char[maxSize];
#             top = -1;
#         }
# 
#         public void push(char j) {
#             stackArray[++top] = j;
#         }
# 
#         public char pop() {
#             return stackArray[top--];
#             }
# 
#             public char peek() {
#                 return stackArray[top];
#             }
# 
#             public boolean isEmpty() {
#                 return (top == -1);
#             }
#         }
# 
#         private Stack theStack;
#         private char[] input;
#         private String output = "";
# 
#     public InToPost(String input) {
#             this.input = input.toCharArray();
#             int stackSize = input.length();
#             theStack = new Stack(stackSize);
#         }
# 
#         public String doTrans() {
#             for (char ch : input) {
#                 switch (ch) {
#                     case '+':
#                     case '-':
#                         gotOper(ch, 1);
#                         break;
#                     case '*':
#                     case '/':
#                         gotOper(ch, 2);
#                         break;
#                     case '(':
#                         theStack.push(ch);
#                         break;
#                     case ')':
#                         gotParen();
#                         break;
#                     default:
#                         output += ch;
#                         break;
#                 }
#             }
#             while (!theStack.isEmpty()) {
#                 output += theStack.pop();
#             }
#             System.out.println(output);
#             return output;
#         }
# 
#         public void gotOper(char opThis, int prec1) {
#             while (!theStack.isEmpty()) {
#                 char opTop = theStack.pop();
#                 if (opTop == '(') {
#                     theStack.push(opTop);
#                     break;
#                 } else {
#                     int prec2;
# 
#                     if (opTop == '+' || opTop == '-')
#                         prec2 = 1;
#                     else
#                         prec2 = 2;
# 
#                     if (prec2 < prec1) {        // 새로 들어올 것이 나보다 우선순위가 높다. -> 스택에 다시 들어가 있자
#                         theStack.push(opTop);
#                         break;
#                     } else                      //  새로온놈이 나보다 우선순위 같거나 낮다 -> 출력에 들어가자
#                     output = output + opTop;
#             }
#         }
#         theStack.push(opThis);
#     }
# 
#     public void gotParen() {
#         while (!theStack.isEmpty()) {
#             char chx = theStack.pop();
#             if (chx == '(')
#                 break;
#             else
#                 output = output + chx;
#         }
#     }
# 
#     public static void main(String[] args) throws IOException {
#         String input = "1+2*4/5-7+3/6";
#         String output;
#         InToPost theTrans = new InToPost(input);
#         output = theTrans.doTrans();
#         System.out.println("Postfix is " + output + '\n');
#     }
# }
```