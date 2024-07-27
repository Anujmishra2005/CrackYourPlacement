# Permutations in array :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/permutations-in-array1747/1)

<h3>
Given two arrays of equal size N and an integer K. The task is to check if after permuting both arrays, we get sum of their corresponding element greater than or equal to k i.e Ai + Bi >= K for all i (from 0 to N-1). Return true if possible, else false.<br><br>

Example 1:<br>

Input : <br>
a[] = {2, 1, 3}, <br>
b[] = { 7, 8, 9 }, <br>
k = 10. <br>
Output : <br>
True<br>
Explanation:<br>
Permutation  a[] = { 1, 2, 3 } <br>
and b[] = { 9, 8, 7 }<br>
satisfied the condition a[i] + b[i] >= K.<br><br>

Example 2:<br>

Input : <br>
a[] = {1, 2, 2, 1}, b[] = { 3, 3, 3, 4 }, k = 5.<br>
Output : <br>
False<br>
Explanation:<br>
Since any permutation won't give the answer.<br>
 
Your Task:  <br><br>
You don't need to read input or print anything. Your task is to complete the function isPossible() which takes the array A[], B[], its size N and an integer K as inputs and returns the answer.<br><br>

Expected Time Complexity: O(N. Log(N))<br>
Expected Auxiliary Space: O(1)<br><br>
 

Constraints:<br><br>
1 ≤ N ≤ 105<br>
1 ≤ K ≤ 1018<br>
1 ≤ Ai, Bi ≤ 1017<br>
  
</h3>

***Solution***

```
class Solution {
  public:
    bool isPossible(long long a[], long long b[], int n, long long k) {
        // Your code goes here
        sort(a,a+n);
        sort(b,b+n);
        reverse(b,b+n);
        for(int i=0; i<n; i++){
                    if(a[i]+b[i]<k) return false;
            }
            return true;
    }
};

```
