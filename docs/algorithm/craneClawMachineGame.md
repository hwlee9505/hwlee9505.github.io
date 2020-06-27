---
layout: default
title: 크레인 인형뽑기 게임 level 1
parent: Algorithm
nav_order: 1
---

# 크레인 인형뽑기 게임 (자료구조 Stack)
{: .no_toc }

---

## 문제 설명

게임개발자인 죠르디는 크레인 인형뽑기 기계를 모바일 게임으로 만들려고 합니다.  
죠르디는 게임의 재미를 높이기 위해 화면 구성과 규칙을 다음과 같이 게임 로직에 반영하려고 합니다.  
게임개발자인 죠르디는 크레인 인형뽑기 기계를 모바일 게임으로 만들려고 합니다.  
죠르디는 게임의 재미를 높이기 위해 화면 구성과 규칙을 다음과 같이 게임 로직에 반영하려고 합니다.  

![](/assets/images/algorithm/craneCrawlMachine1.png)
![](/assets/images/algorithm/craneCrawlMachine2.png)
![](/assets/images/algorithm/craneCrawlMachine3.png)
![](/assets/images/algorithm/craneCrawlMachine4.png)

## 제한 조건

- 시험은 최대 10,000 문제로 구성되어있습니다.
- 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
- 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.


## 입출력 예

| answers      | return            | 
|:-------------|:------------------|
| [1,2,3,4,5]  | [1]               |
| [1,3,2,4,2]  | [1,2,3]           |

## 입출력 예 설명

### 입출력 예 #1

- 수포자 1은 모든 문제를 맞혔습니다.
- 수포자 2는 모든 문제를 틀렸습니다.
- 수포자 3은 모든 문제를 틀렸습니다.

따라서 가장 문제를 많이 맞힌 사람은 수포자 1입니다.

### 입출력 예 #2

- 모든 사람이 2문제씩을 맞췄습니다.

## 해결 전략

![](/assets/images/algorithm/mockTest.jpg)

## 해결 코드1
```yaml
# import java.util.ArrayList;
# class Solution {
#    public int[] solution(int[] answer) {
#       int[] a = {1,2,3,4,5};
#       int[] b = {2,1,2,3,2,4,2,5};
#       int[] c = {3,3,1,1,2,2,4,4,5,5};
#
#       int[] scores = new int[3];
#
#       for(int i = 0 ; i < answers.length; i++){
#           if(answers[i] == a[i%a.length]){
#               scores[0]++;
#           }
#
#           if(answers[i] == b[i%b.length]){
#               scores[1]++;
#           }
#
#           if(answers[i] == c[i%c.length]){
#               scores[2]++;
#           }
#       }
#
#       int max = Math.max(scores[0],Math.max(scores[1],scores[2]));
#
#       ArrayList<Integer> list = new ArrayList<>();
#
#       if(max==scores[0]) list.add(1);
#       if(max==scores[1]) list.add(2);
#       if(max==scores[2]) list.add(3);
#
#       int[] answer = new int[list.size()];
#
#       for(int i = 0 ; i< answer.length; i++){
#           answer[i] = list.get(i);
#       }
#
#       return answer;
#
#    }
# }
```

## 해결 코드2
```yaml
# import java.util.ArrayList;
# class Solution {
#    public int[] solution(int[] answer) {
#        int[] a = {1, 2, 3, 4, 5};
#        int[] b = {2, 1, 2, 3, 2, 4, 2, 5};
#        int[] c = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};
#        int[] score = new int[3];
#        for(int i=0; i<answer.length; i++) {
#            if(answer[i] == a[i%a.length]) {score[0]++;}
#            if(answer[i] == b[i%b.length]) {score[1]++;}
#            if(answer[i] == c[i%c.length]) {score[2]++;}
#        }
#        int maxScore = Math.max(score[0], Math.max(score[1], score[2]));
#        ArrayList<Integer> list = new ArrayList<>();
#        if(maxScore == score[0]) {list.add(1);}
#        if(maxScore == score[1]) {list.add(2);}
#        if(maxScore == score[2]) {list.add(3);}
#        return list.stream().mapToInt(i->i.intValue()).toArray();
#    }
# }
```