# Range Sum of BST :-

[Problem Link] :--- (https://leetcode.com/problems/range-sum-of-bst/description/)

<h3>
Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].<br><br>

Example 1:<br>
Input: root = [10,5,15,3,7,null,18], low = 7, high = 15<br>
Output: 32<br>
Explanation: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.<br><br>
Example 2:<br>


Input: root = [10,5,15,3,7,13,18,1,null,6], low = 6, high = 10<br>
Output: 23<br>
Explanation: Nodes 6, 7, and 10 are in the range [6, 10]. 6 + 7 + 10 = 23.<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 2 * 104].<br>
1 <= Node.val <= 105<br>
1 <= low <= high <= 105<br>
All Node.val are unique.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int rangeSumBST(TreeNode* root, int low, int high) {
        if(root == NULL) return 0;
        int left = rangeSumBST(root->left, low, high);
        int right = rangeSumBST(root->right, low, high);
        if(root->val >= low && root->val <= high){
            return root->val + left+right;
        }
        return left+right;
    }
};

```
