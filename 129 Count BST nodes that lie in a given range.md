# Count BST nodes that lie in a given range :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/1)

<h3>
Given a Binary Search Tree (BST) and a range l-h(inclusive), count the number of nodes in the BST that lie in the given range.<br>
The values smaller than root go to the left side<br>
The values greater and equal to the root go to the right side<br><br>

Example 1:<br>
Input:<br>
      10<br>
     /  \<br>
    5    50<br>
   /    /  \<br>
  1    40  100<br>
l = 5, h = 45<br>
Output: 3<br>
Explanation: 5 10 40 are the node in the range<br><br>
Example 2:<br>

Input:<br>
     5<br>
    /  \<br>
   4    6<br>
  /      \<br>
 3        7<br>
l = 2, h = 8<br>
Output: 5<br>
Explanation: All the nodes are in the given range.<br><br>
Your Task:<br><br>
This is a function problem. You don't have to take input. You are required to complete the function getCountOfNode() that takes root, l ,h as parameters and returns the count.<br><br>

Expected Time Complexity: O(N)<br>
Expected Auxiliary Space: O(Height of the BST).<br><br>

Constraints:<br><br>
1 <= Number of nodes <= 100<br>
1 <= l < h < 103<br><br>
  
</h3>

***Solution***

```

class Solution{
public:
    int cnt=0;
    int getCount(Node *root, int l, int h)
    {
        if(root==NULL) return 0;
        if(root->data>=l && root->data<=h) cnt++;
        getCount(root->left,l,h);
        getCount(root->right,l,h);
        return cnt;
    }
};

```
