---
layout: default
title: N과 M
parent: Algorithm 깊이/너비 우선 탐색
nav_order: 2
---

# N과 M (DFS & Backtracking)

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

자연수 N과 M이 주어졌을 때, 아래 조건을 만족하는 길이가 M인 수열을 모두 구하는 프로그램을 작성하시오.  

* 1부터 N까지 자연수 중에서 중복 없이 M개를 고른 수열  

---

## 입력

첫째 줄에 자연수 N과 M이 주어진다. (1 ≤ M ≤ N ≤ 8)  

---

## 출력

한 줄에 하나씩 문제의 조건을 만족하는 수열을 출력한다. 중복되는 수열을 여러 번 출력하면 안되며, 각 수열은 공백으로 구분해서 출력해야 한다.  

수열은 사전 순으로 증가하는 순서로 출력해야 한다.  

---

## 예제 입력1

```markdown
3 1  
```

## 예제 출력1

```markdown
1  
2  
3  
```

---

## 예제 입력2

```markdown
4 2  
```

## 예제 출력2

```markdown
1 2  
1 3  
1 4  
2 1  
2 3  
2 4  
3 1  
3 2  
3 4  
4 1  
4 2  
4 3  
```

---

## 예제 입력3

```markdown
4 4  
```

## 예제 출력3
```markdown

1 2 3 4  
1 2 4 3  
1 3 2 4  
1 3 4 2  
1 4 2 3  
1 4 3 2  
2 1 3 4  
2 1 4 3  
2 3 1 4  
2 3 4 1  
2 4 1 3  
2 4 3 1  
3 1 2 4  
3 1 4 2  
3 2 1 4  
3 2 4 1  
3 4 1 2  
3 4 2 1  
4 1 2 3  
4 1 3 2  
4 2 1 3  
4 2 3 1  
4 3 1 2  
4 3 2 1  
```

---

## 해결 코드1 (콘솔 바로 출력)
```markdown
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        String str = "";
        new Solution(N, M).backtrack(str);
    }
}

class Solution {

    private int N;
    private int M;
    private StringBuilder sb;

    public Solution(int N, int M) {
        this.N = N;
        this.M = M;
        sb = new StringBuilder();
    }

    public void backtrack(String str) {

        if (M * 2 == str.length()) {
            sb.append(str);
            System.out.println(sb.toString());
            sb = new StringBuilder();

            return;
        }

        for (int i = 1; i <= N; i++) {

            if (str.contains(String.valueOf(i))) {
                continue;
            }

            str += (i + " ");

            backtrack(str);

            str = str.substring(0, str.length() - 2);
        }
    }
}
```

---

## 해결 코드2 (컬렉션에 담고나서 출력)
```markdown
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        // 출력할때 이따가 따로 고쳐 놓기!
        System.out.println(new Solution(N, M).permute().toString());
    }
}

class Solution {

    private int N;
    private int M;
    private StringBuilder sb;

    public Solution(int N, int M) {
        this.N = N;
        this.M = M;
        sb = new StringBuilder();
    }

    public List<List<Integer>> permute() {
        List<List<Integer>> ret = new ArrayList<>();
        List<Integer> tmp = new ArrayList<>();
        backtrack(ret, tmp);
        return ret;
    }

    public void backtrack(List<List<Integer>> ret, List<Integer> tmp) {

        if (M == tmp.size()) {
            ret.add(new ArrayList<Integer>(tmp));
            return;
        }

        for (int i = 1; i <= N; i++) {

            if(tmp.contains(i)){
                continue;
            }

            tmp.add(i);
            backtrack(ret,tmp);
            tmp.remove(tmp.size()-1);
        }
    }
}

```