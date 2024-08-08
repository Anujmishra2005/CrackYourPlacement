# Maximum Width of Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/maximum-width-of-binary-tree/description/)

<h3>
Given the root of a binary tree, return the maximum width of the given tree.
<br>
The maximum width of a tree is the maximum width among all levels.
<br>
The width of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes that would be present in a complete binary tree extending down to that level are also counted into the length calculation.
<br>
It is guaranteed that the answer will in the range of a 32-bit signed integer.<br><br>

Example 1:<br>
Input: root = [1,3,2,5,3,null,9]<br>
Output: 4<br>
Explanation: The maximum width exists in the third level with length 4 (5,3,null,9).<br><br>
Example 2:<br>


Input: root = [1,3,2,5,null,null,9,6,null,7]<br>
Output: 7<br>
Explanation: The maximum width exists in the fourth level with length 7 (6,null,null,null,null,null,7).<br><br>
Example 3:<br>


Input: root = [1,3,2,5]<br>
Output: 2<br>
Explanation: The maximum width exists in the second level with length 2 (3,2).<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 3000].<br>
-100 <= Node.val <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        long long int ans=0;
        if(root==NULL)return 0;
        
        queue<pair<TreeNode*,long long>> q;
        q.push({root,0});

        while(!q.empty()){
            int sz = q.size();
            long long int mini = q.front().second;
            long long int first,last;
            for(int  i =0;i<sz;i++){
                long long cur_idx = q.front().second-mini;
                TreeNode * cur = q.front().first;
                q.pop();
                if(i==0)first = cur_idx;
                if(i==sz-1)last = cur_idx;

                if(cur->left){
                    q.push({cur->left,2*cur_idx+1});
                }
                if(cur->right){
                    q.push({cur->right,2*cur_idx+2});
                }
            } 
            ans = max(ans,last-first+1);           
        }
        return ans;
    }
};

```
