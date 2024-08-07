# Binary Tree Level Order Traversal :-

[Problem Link] :--- (https://leetcode.com/problems/binary-tree-level-order-traversal/)

<h3>
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).<br><br>

Example 1:<br>
Input: root = [3,9,20,null,null,15,7]<br>
Output: [[3],[9,20],[15,7]]<br><br>
Example 2:<br>

Input: root = [1]<br>
Output: [[1]]<br><br>
Example 3:<br>

Input: root = []<br>
Output: []<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 2000].<br>
-1000 <= Node.val <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int levelsOfTree(TreeNode*root){
        if(root==NULL) return 0;
        return 1+max(levelsOfTree(root->left),levelsOfTree(root->right));
    }
    void NthLevel_display(TreeNode*root,int n,int level,vector<int>& v){
        if(root==NULL) return;
        if(n==level){
            v.push_back(root->val);
            return;
        }    
        NthLevel_display(root->left,n+1,level,v);
        NthLevel_display(root->right,n+1,level,v);
    }
    vector<vector<int>> levelOrder(TreeNode* root) {
        int level=levelsOfTree(root);
        vector<vector<int>>ans;
        for(int i=1; i<=level; i++){
            vector<int>v;
            NthLevel_display(root,1,i,v);
            ans.push_back(v);
        }
        return ans;
    }
};

```
