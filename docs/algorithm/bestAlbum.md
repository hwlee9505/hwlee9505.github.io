---
layout: default
title: 베스트앨범 level3 x
parent: Algorithm
nav_order: 22
---

# 베스트앨범 (해시) X

---

## 문제 설명

스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.  
1. 속한 노래가 많이 재생된 장르를 먼저 수록합니다.  
2. 장르 내에서 많이 재생된 노래를 먼저 수록합니다.  
3. 장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.  
노래의 장르를 나타내는 문자열 배열 genres와 노래별 재생 횟수를 나타내는 정수 배열 plays가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.  

## 제한 사항

* genres[i]는 고유번호가 i인 노래의 장르입니다.
* plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
* genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
* 장르 종류는 100개 미만입니다.
* 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
* 모든 장르는 재생된 횟수가 다릅니다.

## 입출력 예

| genres                                |plays                       | return       |
|:--------------------------------------|----------------------------|:-------------|
| [classic, pop, classic, classic, pop] | [500, 600, 150, 800, 2500] | [4, 1, 3, 0] |

## 입출력 예 설명

classic 장르는 1,450회 재생되었으며, classic 노래는 다음과 같습니다.  
* 고유 번호 3: 800회 재생
* 고유 번호 0: 500회 재생
* 고유 번호 2: 150회 재생
pop 장르는 3,100회 재생되었으며, pop 노래는 다음과 같습니다.
* 고유 번호 4: 2,500회 재생
* 고유 번호 1: 600회 재생
따라서 pop 장르의 [4, 1]번 노래를 먼저, classic 장르의 [3, 0]번 노래를 그다음에 수록합니다.  


## 해결 코드1 (다른 분꺼)
```markdown
import java.util.HashMap;
import java.util.ArrayList;
import java.util.Comparator;
import java.util.Iterator;
import java.util.Map;
import java.util.Collections;

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        HashMap<String, Object> genresMap = new HashMap<String, Object>();      //<장르, 곡 정보> 
        HashMap<String, Integer> playMap = new HashMap<String, Integer>(); //<장르, 총 장르 재생수>
        ArrayList<Integer> resultAL = new ArrayList<Integer>();

        for(int i = 0; i < genres.length; i++){
            String key = genres[i];
            HashMap<Integer, Integer> infoMap;       // 곡 정보 : <곡 고유번호, 재생횟수>

            if(genresMap.containsKey(key)){
                 infoMap = (HashMap<Integer, Integer>)genresMap.get(key);
            }
            else {
                infoMap = new HashMap<Integer, Integer>();
            }

            infoMap.put(i, plays[i]);
            genresMap.put(key, infoMap);

            //재생수
            if(playMap.containsKey(key)){
                playMap.put(key, playMap.get(key) + plays[i]);
            }
            else {
                playMap.put(key, plays[i]);
            }
        }

        int mCnt = 0;
        Iterator it = sortByValue(playMap).iterator();

        while(it.hasNext()){
            String key = (String)it.next();
            Iterator indexIt = sortByValue((HashMap<Integer, Integer>)genresMap.get(key)).iterator();
            int playsCnt = 0;

            while(indexIt.hasNext()){
                resultAL.add((int)indexIt.next());
                mCnt++;
                playsCnt++;
                if(playsCnt > 1) break;
            }
        }

        int[] answer = new int[resultAL.size()];

        for(int i = 0; i < resultAL.size(); i++){
            answer[i] = resultAL.get(i).intValue();
        }

        return answer;
    }

    private ArrayList sortByValue(final Map map){
        ArrayList<Object> keyList = new ArrayList();
        keyList.addAll(map.keySet());

        Collections.sort(keyList, new Comparator(){
            public int compare(Object o1, Object o2){
                Object v1 = map.get(o1);
                Object v2 = map.get(o2);

                return ((Comparable) v2).compareTo(v1);
            }
        });

        return keyList;
    }
}
```

## 해결 코드2 (안되는 내꺼)
```markdown
import java.util.*;

class NumberPlays {

    int index;
    int play;

    public NumberPlays(int index, int play) {
        this.index = index;
        this.play = play;
    }

    @Override
    public String toString() {
        return "NumberPlays{" +
                "index=" + index +
                ", play=" + play +
                '}';
    }
}

public class Main {
    
    public int[] solution(String[] genres, int[] plays) {

        // 1. 장르별 총 재생 횟수를 담아 내자
        Map<String, Integer> map = new HashMap();

        // 어떤 장르의 재생횟수가 많은지 sort하기 위해서 ArrayList Collections를 사용 했다.
        ArrayList<Map.Entry> list = new ArrayList<>();


        for (int i = 0; i < genres.length; i++) {

            if (map.get(genres[i]) == null) {
                map.put(genres[i], plays[i]);
            } else {
                int value = map.get(genres[i]) + plays[i];
                map.put(genres[i], value);
            }
        }

        Set set = map.entrySet();
        Iterator it = set.iterator();

        while (it.hasNext()) {
            Map.Entry e = (Map.Entry) it.next();
            list.add(e);
        }

        Collections.sort(list, comparator);

        Stack<NumberPlays>[] stacks = new Stack[list.size()];

        for (int i = 0; i < list.size(); i++) {
            stacks[i] = new Stack<>();
        }

        int index = 0;   //  스택의 인덱스이다.
        for (Map.Entry e : list) {
            for (int i = 0; i < genres.length; i++) {
                if (e.getKey().equals(genres[i])) {
                    stacks[index].push(new NumberPlays(i, plays[i]));
                }
            }
            index++;
        }

        for (int i = 0; i < map.size(); i++) {
            Collections.sort(stacks[i], stackComp);
        }

        ArrayList<Integer> resultList = new ArrayList<>();
        for (int i = 0; i < map.size(); i++) {
            resultList.add(stacks[i].pop().index);
            resultList.add(stacks[i].pop().index);
        }

        int[] answer = new int[resultList.size()];
        int idx = 0;
        for(int i : resultList){

            answer[idx++] = i;

        }

        return answer;
    }

    public Comparator<Map.Entry> comparator = new Comparator<Map.Entry>() {
        @Override
        public int compare(Map.Entry e1, Map.Entry e2) {
            if ((int) e1.getValue() < (int) e2.getValue()) {
                return 1;
            } else if ((int) e1.getValue() > (int) e2.getValue()) {
                return -1;
            } else {
                return 0;
            }
        }
    };

    public Comparator<NumberPlays> stackComp = new Comparator<NumberPlays>() {

        @Override
        public int compare(NumberPlays np1, NumberPlays np2) {
            if (np1.play < np2.play) {
                return -1;
            } else if (np1.play > np2.play) {
                return 1;
            } else {
                return 0;
            }
        }
    };
}

//1 2 4 8 9 11 12 15
```