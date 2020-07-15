---
layout: default
title: 전화번호 목록 level2
parent: Algorithm
nav_order: 20
---

# 전화번호 목록 (해시)
{: .no_toc }

---

## 문제 설명

전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.  
전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.  

* 구조대 : 119
* 박준영 : 97 674 223
* 지영석 : 11 9552 4421

전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.  



## 제한 사항

* phone_book의 길이는 1 이상 1,000,000 이하입니다.
* 각 전화번호의 길이는 1 이상 20 이하입니다.                                                                     location은 0 이상 (현재 대기목록에 있는 작업 수 - 1) 이하의 값을 가지며 대기목록의 가장 앞에 있으면 0, 두 번째에 있으면 1로 표현합니다.

## 입출력 예

| phone_book                          | return     |
|:------------------------------------|:-----------|
| ["119", "97674223", "1195524421"]   | false      |
| ["123","456","789"]                 | true       |
| ["12","123","1235","567","88"]      | false      |

## 입출력 예 설명

### 입출력 예 #1

앞에서 설명한 예와 같습니다.

### 예제 #2

한 번호가 다른 번호의 접두사인 경우가 없으므로, 답은 true입니다.

### 예제 #3

첫 번째 전화번호, “12”가 두 번째 전화번호 “123”의 접두사입니다. 따라서 답은 false입니다.  

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
#         해시문제라 해시는 써야겠고...
#         제대로된 코드는 아닌 거 같다...
# 
#         contains를 쓰면 안된다.
#         접두사를 찾는 것 이기에 contains를 쓰면 안된다.
#         "123", "23"을 생각해보면 된다.
# 
#         startsWith를 사용하자!!
#      */
# 
#     public static void main(String[] args) {
#         System.out.println(Main.solution(new String[]{"119", "97674223", "1195524421"}));
#     }
# 
#     public static boolean solution(String[] phone_book) {
#         boolean answer = true;
# 
#         Map<String, String> map = new HashMap<>();
# 
#         // phone_book의 데이터를 key로 넣고 value를 0으로 default
#         for (String s : phone_book) {
#             map.put(s, s);
#         }
# 
#         Set set = map.entrySet();
#         Iterator it = set.iterator();
# 
#         while (it.hasNext()) {
# 
#             Map.Entry e = (Map.Entry) it.next();
# 
#             for (String s : phone_book) {
# 
#                 if (s.equals(e.getValue())) {
#                     continue;
#                 }
# 
#                 if (s.startsWith((String) e.getValue())) {
#                     return false;
# 
#                 }
#             }
#         }
#         return answer;
#     }
# }
```