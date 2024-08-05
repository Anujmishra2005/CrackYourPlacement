# Sum of Left Leaves :-

[Problem Link] :--- (https://leetcode.com/problems/sum-of-left-leaves/description/)

<h3>
Given the root of a binary tree, return the sum of all left leaves.
<br>
A leaf is a node with no children. A left leaf is a leaf that is the left child of another node.<br><br>
Example 1:<br>
Input: root = [3,9,20,null,null,15,7]<br>
Output: 24<br>
Explanation: There are two left leaves in the binary tree, with values 9 and 15 respectively.<br><br>
Example 2:<br>

Input: root = [1]<br>
Output: 0<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 1000].<br>
-1000 <= Node.val <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {

    void dookie(TreeNode* root, bool is_left, int& ans) {
        if(!root) return;

        if(!root->left && !root->right && is_left) {
            ans += root->val;
        }

        dookie(root->left, true, ans);
        dookie(root->right, false, ans);
    }


public:
    int sumOfLeftLeaves(TreeNode* root) {
        int ans = 0;
        dookie(root, false, ans);

        return ans;
    }
};

```
