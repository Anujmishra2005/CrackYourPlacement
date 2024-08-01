# Minimum Cost Tree From Leaf Values :-

[Problem Link] :--- (https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/description/)

<h3>
Given an array arr of positive integers, consider all binary trees such that:<br>
Each node has either 0 or 2 children;<br>
The values of arr correspond to the values of each leaf in an in-order traversal of the tree.<br>
The value of each non-leaf node is equal to the product of the largest leaf value in its left and right subtree, respectively.<br>
Among all possible binary trees considered, return the smallest possible sum of the values of each non-leaf node. It is guaranteed this sum fits into a 32-bit integer.<br>

A node is a leaf if and only if it has zero children.<br><br>

Example 1:<br>
Input: arr = [6,2,4]<br>
Output: 32<br>
Explanation: There are two possible trees shown.<br>
The first has a non-leaf node sum 36, and the second has non-leaf node sum 32.<br><br>
Example 2:<br>
Input: arr = [4,11]<br>
Output: 44<br><br>
 

Constraints:<br><br>

2 <= arr.length <= 40<br>
1 <= arr[i] <= 15<br>
It is guaranteed that the answer fits into a 32-bit signed integer (i.e., it is less than 231).<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int mctFromLeafValues(vector<int>& arr) {
        int dp[arr.size()][arr.size()];
        int m[arr.size()][arr.size()];
        memset(m,0,sizeof(m));
        for(int g = 0;g<arr.size();g++){
            for(int i=0,j=g;j<arr.size();i++,j++){
                if(g==0){
                    m[i][j] = arr[i];
                }else{
                    m[i][j] = max(m[i][j-1],m[i+1][j]);
                }
            }
        }
    
        
        memset(dp,0,sizeof(dp));
        
        for(int g = 0;g<arr.size();g++){
            for(int i=0,j=g;j<arr.size();i++,j++){
                if(g==0){
                    dp[i][j] = 0;
                }else if(g == 1){
                    dp[i][j] = arr[i]*arr[j];
                }else{
                    int ans = INT_MAX;
                    for(int k = i;k < j;k++){
                         ans = min(ans,dp[i][k] + (m[i][k]*m[k+1][j]) + dp[k+1][j]);
                    }
                    dp[i][j] = ans;
                }
            }
        }
        
        return dp[0][arr.size()-1];
    }
};


```
