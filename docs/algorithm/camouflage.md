---
layout: default
title: 위장 level2
parent: Algorithm
nav_order: 21
---

# 위장 (해시)

---

## 문제 설명

스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.    

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.   

| 종류 | 이름                   |
|:----|:----------------------|
| 얼굴 | 동그란 안경, 검정 선글라스   |
| 상의 | 파란색 티셔츠             |
| 하의 | 청바지                  |
| 겉옷 | 긴 코트                 |

스파이가 가진 의상들이 |담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.  

## 제한 사항

* clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
* 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
* 같은 이름을 가진 의상은 존재하지 않습니다.
* clothes의 모든 원소는 문자열로 이루어져 있습니다.
* 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
* 스파이는 하루에 최소 한 개의 의상은 입습니다.


## 입출력 예

| clothes                                                                                          | return     |
|:-------------------------------------------------------------------------------------------------|:-----------|
| ["yellow_hat", "headgear"], ["blue_sunglasses", "eyewear"], ["green_turban", "headgear"]	       | 5          |
| ["crow_mask", "face"], ["blue_sunglasses", "face"], ["smoky_makeup", "face"]                     | 3          |

## 해결 전략

![](/assets/images/algorithm/bridgeTruck.JPG)
                                                   

## 해결 코드
```yaml
# package bridgeTruck;
# 
# import java.util.LinkedList;
# import java.util.Queue;
# 
# public class MoreBridgeTruck {
# 
#     public static void main(String[] args) {
#         System.out.println(solution(2, 10, new int[]{7, 6, 5, 4}));
#     }
# 
#     public static int solution(int bridgeLength, int weight, int[] truckWeights) {
# 
#         int nowTime = 0;    //  현재시각
#         int totalWeight = 0;    //  다리위의 무게
# 
#         Queue<Truck> waitQ = new LinkedList<>();
#         Queue<Truck> moveQ = new LinkedList<>();
# 
#         for (int i : truckWeights) {
#             Truck t = new Truck(i);
#             waitQ.offer(t);
#         }
# 
#         while (!waitQ.isEmpty() || !moveQ.isEmpty()) {
# 
#             nowTime++;
# 
#             // [1 - 다리위에 지나가는 트럭이 없을 경우]
#             // 1) 다라위의 총무게에 기다리는 다음 트럭 객체의 무게를 더하고
#             // 2) 다리위를 지나는 트럭 큐에 삽입한다.
#             if (moveQ.isEmpty()) {
#                 Truck t = waitQ.poll();
#                 totalWeight += t.weight;
#                 moveQ.offer(t);
#                 continue;
#             }
# 
#             // [2 - 다리위에 지나가는 트럭이 있는 경우]
# 
# 
#             // 1) 다리위를 지나는 트럭의 모든 객체들의 move 속성을 1씩 증가시킨다.
#             for(Truck t : moveQ){
#                 t.moving();
#             }
# 
#             // 조건 2) 다리위를 지나는 트럭 이동반경이 다리길이보다 길다면?
#             // ㄴ 움직이고 있는 트럭의 무게를 다리위 총무게에 뺀다. + moveQ에서도 빼낸다.
#             if(moveQ.peek().move > bridgeLength){
#                 Truck t = moveQ.poll();
#                 totalWeight -= t.weight;
#             }
# 
# 
#             // 조건 3) 기다리는 트럭이 있고 && 다리위 총 무게 + 다음 트럭의 무게 <= 다리가 버틸 수 있는 무게
#             // ㄴ 대기하고 있는 다음 트럭의 무게를 다리위 총 무게에 더하고 다리위를 지나는 큐에 삽입.
# 
#             if(!waitQ.isEmpty() && (totalWeight + waitQ.peek().weight <= weight)){
# 
#                 Truck t = waitQ.poll();
#                 totalWeight += t.weight;
#                 moveQ.offer(t);
#             }
# 
#         }
# 
#         return nowTime;
# 
#     }
# 
# }
# 
# class Truck {
#     int weight;
#     int move;
# 
#     Truck(int weight) {
#         this.weight = weight;
#         this.move = 1;
#     }
# 
#     void moving() {
#         this.move++;
#     }
# 
# }
```