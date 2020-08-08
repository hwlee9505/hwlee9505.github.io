---
layout: default
title: LeetCode Letter Case Permutation x
parent: Algorithm 깊이/너비 우선 탐색
nav_order: 0
---

# LeetCode Letter Case Permutation (BFS & Backtracking) X

[관련 링크](https://www.youtube.com/watch?v=wxQmnEKNXAM){: .btn .fs-5 .mb-4 .mb-md-0 }  


{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

Given a string S, we can transform every letter individually to be lowercase or uppercase to create another string.  Return a list of all possible strings we could create.

## 예시
```markdown
Examples:
Input: S = "a1b2"
Output: ["a1b2", "a1B2", "A1b2", "A1B2"]

Input: S = "3z4"
Output: ["3z4", "3Z4"]

Input: S = "12345"
Output: ["12345"]
```

## 제약

* `S` will be a string with length between `1` and `12`.  
* `S` will consist only of letters or digits.  

## 해결전략

![](/assets/images/algorithm/letterCasePermutation.jpeg)  

## 해결 코드
```markdown
import java.util.ArrayList;
import java.util.List;

public class Main {

    public static void main(String[] args) {
        System.out.println(new Solution().letterCasePermutation("a1b2"));
    }

}

/*
    백트래킹 (재귀 구현)

    조건에 맞는 모든 경우를 찾고싶다.

    조건에 맞는 값을 찾을 때까지 전지
    더 이상 나갈 길이 없으면
    한칸 후퇴

    계속 반복
*/

class Solution {
    public List<String> letterCasePermutation(String S) {
        char[] arr = S.toCharArray();
        List<String> ret = new ArrayList();
        backtrack(arr, ret, 0);
        return ret;
    }
    
    public void backtrack(char[] arr, List<String> ret, int idx){
        
        // length 5, idx 5
        if(idx == arr.length){
            //종료 조건
            ret.add(new String(arr));
        }else{
            char c = arr[idx];
            if(isAlpha(c)){
                arr[idx] = Character.toLowerCase(c);
                backtrack(arr, ret, idx+1);
                arr[idx] = Character.toUpperCase(c);
                backtrack(arr, ret, idx+1);
            }else{
                backtrack(arr, ret, idx+1);
            }
        }
    }
    
    // helper - 문자인지 아닌지 판별 , 반환형 boolean
    public boolean isAlpha(char c){
        return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z');
    }
    
}
```