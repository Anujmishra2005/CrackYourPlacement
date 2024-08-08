# Median of BST :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/median-of-bst/1)

<h3>
Given a Binary Search Tree of size N, find the Median of its Node values.<br><br>

Example 1:<br>
Input:<br>
       6<br>
     /   \<br>
   3      8   <br>
 /  \    /  \<br>
1    4  7    9<br>
Output: 6<br>
Explanation: Inorder of Given BST will be:<br>
1, 3, 4, 6, 7, 8, 9. So, here median will 6.<br><br>

Example 2:<br>

Input:<br>
       6<br>
     /   \<br>
   3      8 <br>  
 /   \    /  <br> 
1    4   7   <br>
Output: 5<br>
Explanation:Inorder of Given BST will be:<br>
1, 3, 4, 6, 7, 8. So, here median will<br>
(4 + 6)/2 = 10/2 = 5.<br><br>
 

Your Task:<br><br>
You don't need to read input or print anything. Your task is to complete the function findMedian() which takes the root of the Binary Search Tree as input and returns the Median of Node values in the given BST.<br>
Median of the BST is:<br><br>

If number of nodes are even: then median = (N/2 th node + (N/2)+1 th node)/2<br>
If number of nodes are odd : then median = (N+1)/2th node.<br><br>

Expected Time Complexity: O(N).<br>
Expected Auxiliary Space: O(Height of the Tree).<br><br>


Constraints:
1<=N<=10000
  
</h3>

***Solution***

```

void fun(struct Node* root,vector<int>&v){
    if(!root){
        return ;
    }
    fun(root->left,v);
    v.push_back(root->data);
    fun(root->right,v);
}
float findMedian(struct Node *root)

{      
      vector<int>v;
      fun(root,v);
      float ans;
      int n=v.size();
      if(n%2==0){
          ans=(float)(v[n/2]+v[(n/2)-1])/2;
          return ans;
      }
      ans=(float)v[n/2];
      return ans;
}


```
