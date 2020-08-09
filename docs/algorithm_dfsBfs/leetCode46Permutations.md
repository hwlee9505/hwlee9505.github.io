---
layout: default
title: Permutations x
parent: Algorithm 깊이/너비 우선 탐색
nav_order: 1
---

# Permutations (BFS & Backtracking) X

[관련 링크](https://www.youtube.com/watch?v=36du-PpTazc){: .btn .fs-5 .mb-4 .mb-md-0 }  


{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

Given a collection of distinct integers, return all possible permutations.  

## 예시
```markdown
Examples:
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

## 해결 코드
```markdown
import java.util.ArrayList;
import java.util.List;

public class Main {

    public static void main(String[] args) {
        System.out.println(new Solution().permute(new int[]{1,2,3,4,5}));
    }
}


class Solution {

    // ex input: 1,2,3
    // call 0: add 1
    // call 1: skip 1, add 2 // 1,2
    // call 2: skip 1, skip:2 // add 3 // 1,2,3
    // call 3: base case, 1,2,3 -> add to ret

    // call 2: remove 3. return // 1,2
    // call 1: remove 2, add 3 // 1,3
    // call 4: skip 1, add 2 // 1,3,2
    // call 5: base case, 1,3,2 -> add to ret
    // call 4: remove 2, skip 3 return // 1,3 -> // 2,1,3....

    public List<List<Integer>> permute(int[] nums) {

        List<List<Integer>> ret = new ArrayList<>();
        List<Integer> tmp = new ArrayList<>();
        backtrack(nums, ret, tmp);
        return ret;
    }

    public void backtrack(int[] nums, List<List<Integer>> ret, List<Integer> tmp) {

        // base case
        if(tmp.size() == nums.length){
            ret.add(new ArrayList<Integer>(tmp));
            return;
        }

        // recursion
        for(int num : nums){
            // 중복은 제거
            if(tmp.contains(num)) continue;;

            tmp.add(num);
            backtrack(nums, ret, tmp);
            tmp.remove(tmp.size()-1);
        }


    }
}
```