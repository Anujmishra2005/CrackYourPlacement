# Allocate Minimum Pages :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

<h3>
You have n books, each with arr[i] a number of pages. m students need to be allocated contiguous books, with each student getting at least one book.
Out of all the permutations, the goal is to find the permutation where the sum of the maximum number of pages in a book allotted to a student should be the minimum, out of all possible permutations.
<br><br>
Note: Return -1 if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).<br><br>
Examples:<br><br>
Input: n = 4, arr[] = [12, 34, 67, 90], m = 2<br>
Output: 113<br>
Explanation: Allocation can be done in following ways:<br>
{12} and {34, 67, 90} Maximum Pages = 191<br>
{12, 34} and {67, 90} Maximum Pages = 157<br>
{12, 34, 67} and {90} Maximum Pages =113.<br>
Therefore, the minimum of these cases is 113, which is selected as the output.<br>
Input: n = 3, arr[] = [15, 17, 20], m = 5<br>
Output: -1<br>
Explanation: Allocation can not be done.<br<br>
Expected Time Complexity: O(n logn)<br>
Expected Auxilliary Space: O(1)<br><br>
 
Constraints:<br><br>
1 <=  n, m <= 105<br>
1 <= arr[i] <= 106<br>   
  
</h3>

***Solution***

```

class Solution {
  public:
    bool possible(int v[], long long mid, int member, int n){
    int cnt = 0;
    int running = 0;
    for(int i = 0; i < n; i++){
        running += v[i];
        
        if(running > mid){
            cnt++;
            running = v[i];
        }
    }
    return cnt >= member;
}
    long long findPages(int n, int arr[], int m) {
        long long start = INT_MIN, end = 0;
        if(n < m)
            return -1;
        for(int i = 0; i < n; i++){
            long long v = arr[i];
            start = max(start, v);
            end += v;
        }
        while(start <= end){
            long long mid = start + (end - start) / 2;
            if(possible(arr, mid, m, n))
                start = mid + 1;
            else
                end = mid - 1;
        }
        return start;
    }
};

```
