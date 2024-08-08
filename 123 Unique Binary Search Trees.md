# Unique Binary Search Trees :-

[Problem Link] :--- (https://leetcode.com/problems/unique-binary-search-trees/description/)

<h3>
Given an integer n, return the number of structurally unique BST's (binary search trees) which has exactly n nodes of unique values from 1 to n.<br><br>

Example 1:<br>
Input: n = 3<br>
Output: 5<br><br>
Example 2:<br>

Input: n = 1<br>
Output: 1<br><br>
 

Constraints:<br><br>

1 <= n <= 19<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int numTrees(int n) {
        if(n <= 1) return 1;
        int ans = 0;
        for(int i = 1; i <= n; i++) 
            ans += numTrees(i-1) * numTrees(n-i);
        return ans;
    }
};

```
