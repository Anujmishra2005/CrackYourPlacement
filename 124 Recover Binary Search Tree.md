# Recover Binary Search Tree :-

[Problem Link] :--- (https://leetcode.com/problems/recover-binary-search-tree/)

<h3>
You are given the root of a binary search tree (BST), where the values of exactly two nodes of the tree were swapped by mistake. Recover the tree without changing its structure.<br><br>

Example 1:<br>
Input: root = [1,3,null,null,2]<br>
Output: [3,1,null,null,2]<br>
Explanation: 3 cannot be a left child of 1 because 3 > 1. Swapping 1 and 3 makes the BST valid.<br><br>
Example 2:<br>


Input: root = [3,1,4,null,null,2]<br>
Output: [2,1,4,null,null,3]<br>
Explanation: 2 cannot be in the right subtree of 3 because 2 < 3. Swapping 2 and 3 makes the BST valid.<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [2, 1000].<br>
-231 <= Node.val <= 231 - 1<br><br>
 

Follow up: A solution using O(n) space is pretty straight-forward. Could you devise a constant O(1) space solution?<br><br>
  
</h3>

***Solution***

```
class Solution {
private: 
    TreeNode* first;
    TreeNode* prev;
    TreeNode* middle;
    TreeNode* last; 
private: 
    void inorder(TreeNode* root) {//iterating the inorder sorted array(which should be sorted)
        if(root == NULL) return; 
        
        inorder(root->left);
        
        if (prev != NULL && (root->val < prev->val))
        {
           
            // If this is first violation, mark these two nodes as
            // 'first' and 'middle'
            if ( first == NULL )
            {
                first = prev;
                middle = root;
            }
 
            // If this is second violation, mark this node as last
            else
                last = root;
        }
 
        // Mark this node as previous
        prev = root;
        inorder(root->right); 
    }
public:
    void recoverTree(TreeNode* root) {
        first = middle = last = NULL; 
        prev = new TreeNode(INT_MIN); 
        inorder(root);
        if(first && last) swap(first->val, last->val); 
        else if(first && middle) swap(first->val, middle->val); 
    }
};

```
