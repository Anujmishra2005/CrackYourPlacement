# Maximum of minimum for every window size :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/maximum-of-minimum-for-every-window-size3453/1)

<h3>
Given an integer array. The task is to find the maximum of the minimum of every window size in the array.
Note: Window size varies from 1 to the size of the Array.<br><br>

Example 1:<br>
Input:<br>
N = 7<br>
arr[] = {10,20,30,50,10,70,30}<br>
Output: 70 30 20 10 10 10 10 <br>
Explanation: <br>
1.First element in output
indicates maximum of minimums of all
windows of size 1.<br>
2.Minimums of windows of size 1 are {10},
 {20}, {30}, {50},{10}, {70} and {30}. 
 Maximum of these minimums is 70. <br>
3. Second element in output indicates
maximum of minimums of all windows of
size 2. <br>
4. Minimums of windows of size 2
are {10}, {20}, {30}, {10}, {10}, and
{30}.<br>
5. Maximum of these minimums is 30 
Third element in output indicates
maximum of minimums of all windows of
size 3. <br>
6. Minimums of windows of size 3
are {10}, {20}, {10}, {10} and {10}.<br>
7.Maximum of these minimums is 20. 
Similarly other elements of output are
computed.<br><br>
Example 2:<br>

Input:<br>
N = 3<br>
arr[] = {10,20,30}<br>
Output: 30 20 10<br>
Explanation: First element in output
indicates maximum of minimums of all
windows of size 1.Minimums of windows
of size 1 are {10} , {20} , {30}.
Maximum of these minimums are 30 and
similarly other outputs can be computed<br>
Your Task:<br><br>
The task is to complete the function maxOfMin() which takes the array arr[] and its size N as inputs and finds the maximum of minimum of every window size and returns an array containing the result. 
<br><br>
Expected Time Complxity : O(N)<br>
Expected Auxilliary Space : O(N)<br><br>

Constraints:<br><br>
1 <= N <= 105<br>
1 <= arr[i] <= 106<br>
  
</h3>

***Solution***

```

class Solution
{
    public:
    //Function to find maximum of minimums of every window size.
    vector < int > maxOfMin(int arr[], int n) {
  stack < int > st;
  int left[n + 1], right[n + 1];
  vector < int > ans(n + 1);
  for (int i = 0; i < n; i++) {
    left[i] = -1;
    right[i] = n;
  }
  for (int i = 0; i < n; i++) {
    while (!st.empty() && arr[st.top()] >= arr[i]) st.pop();
    if (!st.empty()) left[i] = st.top();
    st.push(i);
  }
  while (!st.empty()) st.pop();
  for (int i = n - 1; i >= 0; i--) {
    while (!st.empty() && arr[st.top()] >= arr[i]) st.pop();
    if (!st.empty()) right[i] = st.top();
    st.push(i);
  }
  for (int i = 0; i <= n; i++) ans[i] = 0;
  for (int i = 0; i < n; i++) {
    int len = right[i] - left[i] - 1;
    ans[len] = max(ans[len], arr[i]);
  }
  for (int i = n - 1; i >= 0; i--) {
    ans[i] = max(ans[i], ans[i + 1]);
  }
  ans.erase(ans.begin());
  return ans;
}
};

```
