# Binary Tree Inorder Traversal :-

[Problem Link] :--- (https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

<h3>
Given the root of a binary tree, return the inorder traversal of its nodes' values.<br><br>

Example 1:<br>
Input: root = [1,null,2,3]<br>
Output: [1,3,2]<br><br>
Example 2:<br>

Input: root = []<br>
Output: []<br><br>
Example 3:<br>

Input: root = [1]<br>
Output: [1]<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 100].<br>
-100 <= Node.val <= 100<br><br>
 

Follow up: Recursive solution is trivial, could you do it iteratively?<br><br>
  
</h3>

***Solution***

```


class Solution {
public:
    void inOrder(TreeNode* root,vector<int>& ans){
        if(root==NULL) return;
        inOrder(root->left,ans);
        ans.push_back(root->val);
        inOrder(root->right,ans);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>ans;
        inOrder(root,ans);
        return ans;
    }
};

```
