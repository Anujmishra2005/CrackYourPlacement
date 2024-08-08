# Flatten Binary Tree to Linked List :-

[Problem Link] :--- (https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/)

<h3>
Given the root of a binary tree, flatten the tree into a "linked list":
<br>
The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.<br>
The "linked list" should be in the same order as a pre-order traversal of the binary tree.<br><br>

Example 1:<br>
Input: root = [1,2,5,3,4,null,6]<br>
Output: [1,null,2,null,3,null,4,null,5,null,6]<br><br>
Example 2:<br>

Input: root = []<br>
Output: []<br><br>
Example 3:<br>

Input: root = [0]<br>
Output: [0]<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 2000].<br>
-100 <= Node.val <= 100<br><br>
 

Follow up: Can you flatten the tree in-place (with O(1) extra space)?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    void flatten(TreeNode* root) {
        while(root)
        {
            if(!root->left)
            {
                root=root->right;
            }
            else
            {
                TreeNode * current= root->left;
                while(current->right)
                {
                    current = current -> right ;
                }
                current -> right =root->right;
                root->right = root->left;
                root->left=nullptr;
                root=root->right;                
            }

        }
        
    }
};

```
