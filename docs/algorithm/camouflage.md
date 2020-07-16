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

스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.  

## 제한 사항

* clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
* 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
* 같은 이름을 가진 의상은 존재하지 않습니다.
* clothes의 모든 원소는 문자열로 이루어져 있습니다.
* 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
* 스파이는 하루에 최소 한 개의 의상은 입습니다.

## 입출력 예 설명

### 예제 #1

headgear에 해당하는 의상이 yellow_hat, green_turban이고 eyewear에 해당하는 의상이 blue_sunglasses이므로 아래와 같이 5개의 조합이 가능합니다.   

1. yellow_hat  
2. blue_sunglasses  
3. green_turban  
4. yellow_hat + blue_sunglasses  
5. green_turban + blue_sunglasses  

### 예제 #2

face에 해당하는 의상이 crow_mask, blue_sunglasses, smoky_makeup이므로 아래와 같이 3개의 조합이 가능합니다.  

1. crow_mask
2. blue_sunglasses
3. smoky_makeup

## 해결 코드
```yaml
# import java.util.HashMap;
# import java.util.Iterator;
# import java.util.Map;
# import java.util.Set;
# 
# public class Main {
# 
#     /*
#         1) -- ●, ○            ==      2개
#         2) -- A, B, C         ==      3개
#         3) -- ㄱ, ㄴ           ==      2개
# 
#         있다고 할 떄
#         최소 하나 라도 쓰고 있는 모든 경우의 수는?
# 
#         result = (2 + 1) * ( 3 + 1 ) * (2 + 1) - 1;
#      */
# 
# 
#     public static void main(String[] args) {
#         System.out.println(solution(new String[][]{{"yellow_hat", "headgear"}, {"blue_sunglasses", "eyewear"}, {"green_turban", "headgear"}}));
#     }
# 
#     public static int solution(String[][] clothes) {
# 
#         Map<String, Integer> map = new HashMap<>();
# 
#         // 맵에 키값이 중복 불가 이므로 중복 생각은 안해도 된다.
#         for(int i = 0 ; i < clothes.length; i++){
# 
#             String tempKey = clothes[i][1];
#             if(map.get(tempKey) == null) {
#                 map.put(tempKey, 1);
#             }else{
#                 // 완주하지 못한 선수들에서 썼던 로직인데 이제 좀 기억해라
#                 int value = map.get(tempKey) + 1;
#                 map.put(tempKey, value);
#             }
#         }
# 
#         int[] temp = new int[map.size()];
#         int index = 0;
# 
#         Set set = map.entrySet();
#         Iterator it = set.iterator();
# 
#         while(it.hasNext()){
#             Map.Entry e = (Map.Entry) it.next();
# 
#             temp[index++] = (Integer) e.getValue() + 1;
#         }
# 
#         int result = 1;
#         for(int i : temp){
#             result *= i;
#         }
# 
#         return result -1;
#     }
# }
```