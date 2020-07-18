---
layout: default
title: 완주하지 못한 선수 level1
parent: Algorithm 해시
nav_order: 0
---

# 완주하지 못한 선수 (해시)
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.  
마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.  

## 제한 조건

* 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
* completion의 길이는 participant의 길이보다 1 작습니다.
* 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
* 참가자 중에는 동명이인이 있을 수 있습니다.

## 입출력 예

| participant                                        | completion                                        | return            | 
|:---------------------------------------------------|:--------------------------------------------------|:------------------|
| ["leo", "kiki", "eden"]                            | ["eden", "kiki"]                                  | "leo"             |
| ["marina", "josipa", "nikola", "vinko", "filipa"]  | ["marina", "josipa", "nikola", "vinko", "filipa"] | "vinko"           |
| [mislav, stanko, mislav, ana]                      | ["stanko", "ana", "mislav"]                       | "mislav"          |

## 입출력 예 설명

### 입출력 예 #1

"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

### 입출력 예 #2

"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

### 입출력 예 #2

"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.

## 해결 코드1
```java
import java.util.HashMap;
import java.util.Map;
class Solution {
    public String solution(String[] participant, String[] completion) {
             
         String answer = "";
        int val = 0;

        Map<String, Integer> map = new HashMap<>();

        for(String part : participant){
            // 지정된 키(key)의 값(객체)을 반환, 못찾으면 null 반환
            if(map.get(part) == null){
                map.put(part,1);
            }else{
                // map의 value값을 +1로 만든다.
                val = map.get(part)+1;
                map.put(part,val);
            }
        }

        // 다시 선수들 중에 완주한 놈들의 value를 -1 해버리기
        for(String comp : completion){
            val = map.get(comp) -1;
            map.put(comp,val);
        }

        for(String key: map.keySet()){
            if(map.get(key) == 1){
                answer = key;
            }
        }

        return answer;
    }
}
```

## 해결 코드2
```java
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i;
        for ( i=0; i<completion.length; i++){

            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        return participant[i];
    }
}
```