# Unique Binary Search Trees II :-

[Problem Link] :--- (https://leetcode.com/problems/unique-binary-search-trees-ii/description)

<h3>
Given an integer n, return all the structurally unique BST's (binary search trees), which has exactly n nodes of unique values from 1 to n. Return the answer in any order.<br><br>

Example 1:<br>
Input: n = 3<br>
Output: [[1,null,2,null,3],[1,null,3,2],[2,1,3],[3,1,null,null,2],[3,2,null,1]]<br><br>
Example 2:<br>

Input: n = 1<br>
Output: [[1]]<br><br>

Constraints:<br><br>

1 <= n <= 8<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    vector<TreeNode*> generateTrees(int n) {
        return n ? generate_trees(1, n) : vector<TreeNode*>();
    }

private:
    vector<TreeNode*> generate_trees(int start, int end) {
        if (start > end) return {nullptr};

        vector<TreeNode*> all_trees;
        for (int i = start; i <= end; i++) {
            vector<TreeNode*> left_trees = generate_trees(start, i - 1);
            vector<TreeNode*> right_trees = generate_trees(i + 1, end);

            for (TreeNode* l : left_trees) {
                for (TreeNode* r : right_trees) {
                    TreeNode* current_tree = new TreeNode(i);
                    current_tree->left = l;
                    current_tree->right = r;
                    all_trees.push_back(current_tree);
                }
            }
        }
        return all_trees;
    }
};

```
