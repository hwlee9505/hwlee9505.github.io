---
layout: default
title: Sum of Left Leaves
parent: Algorithm 깊이/너비 우선 탐색
nav_order: 3
---

# LeetCode Sum of Left Leaves (BFS)

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 문제 설명

Find the sum of all left leaves in a given binary tree.  

```markdown
      3  
     / \
    9  20
      /  \
     15   7
```

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.  

---

## 해결 코드
```markdown
class TreeNode {

    int value;
    TreeNode left;
    TreeNode right;

    public TreeNode() {
    }

    public TreeNode(int value, TreeNode left, TreeNode right) {
        this.value = value;
        this.left = left;
        this.right = right;
    }
}

class Solution {

    int sum = 0;

    public int sumOfLeftLeaves(TreeNode root) {

        if (root != null) {
            traverse(root);
        }
        return sum;
    }

    public boolean traverse(TreeNode root) {

        if (root.left != null) {
            boolean isLeaf = traverse(root.left);
            if (isLeaf) {
                sum += root.left.value;
            }
        }
        if (root.right != null) {
            traverse(root.right);
        }
        
        return root.left == null && root.right == null;
    }
}

public class Main {

    public static void main(String[] args) {
        TreeNode node4 = new TreeNode(7,null,null);
        TreeNode node3 = new TreeNode(15,null,null);
        TreeNode node2 = new TreeNode(20,node3,node4);
        TreeNode node1 = new TreeNode(9,null,null);
        TreeNode root = new TreeNode(3,node1,node2);

        System.out.println(new Solution().sumOfLeftLeaves(root));
    }
}
```