# Path Sum III :-

[Problem Link] :--- (https://leetcode.com/problems/path-sum-iii/)

<h3>
Given the root of a binary tree and an integer targetSum, return the number of paths where the sum of the values along the path equals targetSum.
<br><br>
The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).<br><br>

Example 1:<br>
Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8<br>
Output: 3<br>
Explanation: The paths that sum to 8 are shown.<br><br>
Example 2:<br>

Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22<br>
Output: 3<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 1000].<br>
-109 <= Node.val <= 109<br>
-1000 <= targetSum <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    unordered_map<long , int> mp;
    int count=0;
    void dfs(TreeNode* root, int targetSum,long prefix_sum){
        if(!root) return ;
        prefix_sum+=root->val;
        if(mp.find(prefix_sum-targetSum)!=mp.end()){
            count+=mp[prefix_sum-targetSum];
        }
        mp[prefix_sum]++;
        dfs(root->left, targetSum, prefix_sum);
        dfs(root->right, targetSum, prefix_sum);
        mp[prefix_sum]--;
    }
    int pathSum(TreeNode* root, int targetSum) {
        mp[0]=1;
        dfs(root, targetSum,0);
        return count;
        
    }
};

```
