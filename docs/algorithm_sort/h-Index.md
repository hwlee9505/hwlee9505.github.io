---
layout: default
title: H-Index level 2 x
parent: Algorithm 정렬
nav_order: 2
---

# H-Index (정렬) X
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

## 문제 설명

H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다.  
어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다.  
위키백과1에 따르면, H-Index는 다음과 같이 구합니다.  
어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.  
어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.  

## 제한 사항

* 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.  
* 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.  

## 입출력 예

| citations                 | return                  |
|:--------------------------|:------------------------|
| [3, 0, 6, 1, 5]           | 3                       |

## 입출력 예 설명                                  

이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다.  
그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.  

## 해결 코드
```java
import java.util.Arrays;
import java.util.Collections;

public class Main {

    public static void main(String[] args) {
        System.out.println(Main.solution(new int[]{3, 0, 6, 1, 5}));
    }

    public static int solution(int[] citations) {

        Integer[] cArr = new Integer[citations.length];

        int idx = 0;
        for (int c : citations) {
            cArr[idx++] = c;
        }

        Arrays.sort(cArr, Collections.reverseOrder());

        for(int i = 0 ; i < cArr.length; i++){
            if(cArr[i] < i +1) return i;        // 인용된 논문 수가 i+1(편) 보다 작아질 때 i를 return 합니다.
        }

        return cArr.length;
    }
}
```