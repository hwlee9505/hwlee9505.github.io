---
layout: default
title: 다리위를 지나는 트럭 level2
parent: stackQueue
nav_order: 2
---

# 다리위를 지나는 트럭 (자료구조 Queue)
{: .no_toc }

---

## 문제 설명

트럭 여러 대가 강을 가로지르는 일 차선 다리를 정해진 순으로 건너려 합니다. 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다. 트럭은 1초에 1만큼 움직이며, 다리 길이는 bridge_length이고 다리는 무게 weight까지 견딥니다.  
※ 트럭이 다리에 완전히 오르지 않은 경우, 이 트럭의 무게는 고려하지 않습니다.

예를 들어, 길이가 2이고 10kg 무게를 견디는 다리가 있습니다.  
무게가 [7, 4, 5, 6]kg인 트럭이 순서대로 최단 시간 안에 다리를 건너려면 다음과 같이 건너야 합니다.트럭 여러 대가 강을 가로지르는 일 차선 다리를 정해진 순으로 건너려 합니다.  
모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다.  
트럭은 1초에 1만큼 움직이며, 다리 길이는 bridge_length이고 다리는 무게 weight까지 견딥니다.

| 경과 시간       | 다리를 지난 트럭      | 다리를 건너는 트럭     | 대기 트럭           | 
|:-------------|:------------------|:------------------|:------------------|
| 0            | []                | []                | [7,4,5,6]         |
| 1~2          | []                | [7]               | [4,5,6]           |
| 3            | [7]               | [4]               | [5,6]             |
| 4            | [7]               | [4,5]             | [6]               |
| 5            | [7,4]             | [5]               | [6]               |
| 6~7          | [7,4,5]           | [6]               | []                |
| 8            | [7,4,5,6]         | []                | []                |

따라서, 모든 트럭이 다리를 지나려면 최소 8초가 걸립니다.   
solution 함수의 매개변수로 다리 길이 bridge_length, 다리가 견딜 수 있는 무게 weight, 트럭별 무게 truck_weights가 주어집니다.   
이때 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 return 하도록 solution 함수를 완성하세요.

## 제한 조건

- bridge_length는 1 이상 10,000 이하입니다.
- weight는 1 이상 10,000 이하입니다.
- truck_weights의 길이는 1 이상 10,000 이하입니다.
- 모든 트럭의 무게는 1 이상 weight 이하입니다.


## 입출력 예

| bridge_length| weight            | truck_weights                    | return     | 
|:-------------|:------------------|:---------------------------------|:-----------|
| 2            | 10                | [7,4,5,6]                        | 8          |
| 100          | 100               | [10]                             | 101        |
| 100          | 100               | [10,10,10,10,10,10,10,10,10,10,] | 110        |

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