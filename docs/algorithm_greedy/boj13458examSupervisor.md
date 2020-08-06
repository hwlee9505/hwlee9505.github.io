---
layout: default
title: BOJ 시험감독
parent: Algorithm 탐욕법
nav_order: 1
---
# BaekJoon 13458 / 시험감독(그리디 알고리즘)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

총 N개의 시험장이 있고, 각각의 시험장마다 응시자들이 있다. i번 시험장에 있는 응시자의 수는 Ai명이다.  

감독관은 총감독관과 부감독관으로 두 종류가 있다. 총감독관은 한 시험장에서 감시할 수 있는 응시자의 수가 B명이고, 부감독관은 한 시험장에서 감시할 수 있는 응시자의 수가 C명이다.  

각각의 시험장에 총감독관은 오직 1명만 있어야 하고, 부감독관은 여러 명 있어도 된다.  

각 시험장마다 응시생들을 모두 감시해야 한다. 이때, 필요한 감독관 수의 최솟값을 구하는 프로그램을 작성하시오.  

---

## 입력

첫째 줄에 시험장의 개수 N(1 ≤ N ≤ 1,000,000)이 주어진다.  

둘째 줄에는 각 시험장에 있는 응시자의 수 Ai (1 ≤ Ai ≤ 1,000,000)가 주어진다.  

셋째 줄에는 B와 C가 주어진다. (1 ≤ B, C ≤ 1,000,000)  

---

## 출력

각 시험장마다 응시생을 모두 감독하기 위해 필요한 감독관의 최소 수를 출력한다.

---

### 입력 예시1

3  
3 4 5  
2 2  

### 출력 예시1

7  

---

### 입력 예시2

5  
10 9 10 9 10  
7 20  

### 출력 예시2

10  

---

## 해결 코드1
```markdown
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    /**     이중 배열을 쓰면 안된다. O(n^2) X
     *
     * 1. siteNum      == 시험장
     * 2. candidate[]  == 각 시험장 응시생 수
     * 3. totalSV      == 총 감독관 몇 명까지 가능 수
     * 4. deputySV     == 부 감독관 몇 명까지 가능 수
     */

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int siteNum = Integer.parseInt(br.readLine());
        int[] candidate = new int[siteNum];
        StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < siteNum; i++) {
            candidate[i] = Integer.parseInt(st.nextToken());
        }
        st = new StringTokenizer(br.readLine());
        int totalSV = Integer.parseInt(st.nextToken());
        int deputySV = Integer.parseInt(st.nextToken());

        long answer = 0;                // 왜 기본자료형이 long이여야 하는지는 의문...
        for (int i = 0; i < siteNum; i++) {

            // 총감독관은 오직 1명은 있어야하기 때문에 일단 빼준다.
            candidate[i] -= totalSV;
            answer++;

            // 부감독관으로 나머지 채우기
            if (candidate[i] > 0) {

                answer += candidate[i] / deputySV;

                if (candidate[i] % deputySV != 0) {
                    answer++;
                }

            }

        }
        System.out.println(answer);
    }
}
```

---

## 해결 코드2 (시간초과 코드)
```markdown
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    /**
     *
     * 1. siteNum      == 시험장
     * 2. candidate[]  == 각 시험장 응시생 수
     * 3. totalSV      == 총 감독관 몇 명까지 가능 수
     * 4. deputySV     == 부 감독관 몇 명까지 가능 수
     */

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int siteNum = Integer.parseInt(br.readLine());
        int[] candidate = new int[siteNum];
        StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < siteNum; i++) {
            candidate[i] = Integer.parseInt(st.nextToken());
        }
        st = new StringTokenizer(br.readLine());
        int totalSV = Integer.parseInt(st.nextToken());
        int deputySV = Integer.parseInt(st.nextToken());

        int answer = 0;
        for (int i = 0; i < siteNum; i++) {

            // 총감독관은 오직 1명은 있어야하기 때문에 일단 빼준다.
            candidate[i] -= totalSV;
            answer++;

            if (candidate[i] <= 0) {
                break;
            }

            while (candidate[i] > 0) {
                candidate[i] -= deputySV;
                answer++;
            }
        }
        System.out.println(answer);
    }
}
```