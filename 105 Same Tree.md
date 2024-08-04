# Same Tree :-

[Problem Link] :--- (https://leetcode.com/problems/same-tree/description/)

<h3>
Given the roots of two binary trees p and q, write a function to check if they are the same or not.
<br><br>
Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.<br><br>

Example 1:<br>
Input: p = [1,2,3], q = [1,2,3]<br>
Output: true<br><br>
Example 2:<br>


Input: p = [1,2], q = [1,null,2]<br>
Output: false<br><br>
Example 3:<br>


Input: p = [1,2,1], q = [1,1,2]<br>
Output: false<br><br>
 

Constraints:<br><br>

The number of nodes in both trees is in the range [0, 100].<br>
-104 <= Node.val <= 104<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
       if(p==NULL && q==NULL) return true;
       if(p==NULL || q==NULL) return false;
       if(p->val!=q->val) return false;
       return isSameTree(p->left,q->left)   && isSameTree(p->right,q->right);
    }

};

```
