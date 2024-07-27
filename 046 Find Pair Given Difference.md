#  Find Pair Given Difference :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/find-pair-given-difference1559/1)

<h3>
Given an array arr[] of size n and an integer x, return 1 if there exists a pair of elements in the array whose absolute difference is x, otherwise, return -1..<br><br>

Example 1:<br>
Input:<br>
n = 6<br>
x = 78<br>
arr[] = {5, 20, 3, 2, 5, 80}<br>
Output:<br>
1<br>
Explanation:<br>
Pair (2, 80) have absolute difference of 78.<br><br>
Example 2:<br>

Input:<br>
n = 5<br>
x = 45<br>
arr[] = {90, 70, 20, 80, 50}<br>
Output:<br>
-1<br>
Explanation:<br>
There is no pair with absolute difference of 45.<br>
 
Your Task:<br>
You need not take input or print anything. Your task is to complete the function findPair() which takes integers n, x, and an array arr[] as input parameters and returns 1 if the required pair exists, return -1 otherwise.
<br>
Expected Time Complexity: O(n* Log(n)).<br>
Expected Auxiliary Space: O(1).<br>
<br>
Constraints:<br><br>
1<=n<=106 <br>
1<=arr[i]<=106 <br>
0<=x<=105<br>
  
</h3>

***Solution***

```

class Solution {
  public:
    int findPair(int n, int x, vector<int> &arr) {
        sort(arr.begin(), arr.end());
        int i = 0, j = 1;
        while (i < n && j < n) 
        {
            if (i != j && arr[j] - arr[i] == x) 
            {
                return 1;
            } 
            else if (arr[j] - arr[i] < x) 
            {
                j++;
            } 
            else 
            {
                i++;
            }
        }
        return -1;
       
        // code here
    }
};

```
