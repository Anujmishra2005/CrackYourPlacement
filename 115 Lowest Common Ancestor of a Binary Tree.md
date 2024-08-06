#  Lowest Common Ancestor of a Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

<h3>
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.
<br><br>
According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”.<br><br>

Example 1:<br>
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1<br>
Output: 3<br>
Explanation: The LCA of nodes 5 and 1 is 3.<br><br>
Example 2:<br>
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4<br>
Output: 5<br>
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.<br><br>
Example 3:<br>
Input: root = [1,2], p = 1, q = 2<br>
Output: 1<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [2, 105].<br>
-109 <= Node.val <= 109<br>
All Node.val are unique.<br>
p != q<br>
p and q will exist in the tree.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL)
            return NULL;
        root->left = lowestCommonAncestor(root->left,p,q);
        root->right = lowestCommonAncestor(root->right,p,q);
        if(root->val==p->val || root->val==q->val)
            return root;
        if(root->left && root->right)
            return root;
        return root->left==NULL ? root->right : root->left;
    }
};

```
