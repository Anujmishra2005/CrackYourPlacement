# All Unique Permutations of an array :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/all-unique-permutations-of-an-array/0)

<h3>
Given an array arr[] of length n. Find all possible unique permutations of the array in sorted order. A sequence A is greater than sequence B if there is an index i for which Aj = Bj for all j<i and Ai > Bi..<br><br>

Example 1:<br>
Input: <br>
n = 3<br>
arr[] = {1, 2, 1}<br>
Output: <br>
1 1 2<br>
1 2 1<br>
2 1 1<br>
Explanation:<br>
These are the only possible unique permutations for the given array.<br><br>
Example 2:<br>
Input: <br>
n = 2<br>
arr[] = {4, 5}<br>
Output: <br>
Only possible 2 unique permutations are<br>
4 5<br>
5 4<br><br>
 
Your Task:<br>
You don't need to read input or print anything. You only need to complete the function uniquePerms() that takes an integer n, and an array arr of size n as input and returns a sorted list of lists containing all unique permutations of the array.<br>
<br>
Expected Time Complexity:  O(n*n!)<br>
Expected Auxilliary Space: O(n*n!)<br>

Constraints:
1 ≤ n ≤ 9
  
</h3>

***Solution***

```
class Solution {
  public:
    unordered_set<string> st;
    vector<vector<int>> result;
    int N;
    
    
    void solve(vector<int> &arr, vector<int>& temp, vector<bool>& used) {
        if(temp.size() == N) {
            string s = "";
            for(int &x : temp) {
                s += to_string(x);
            }
            if(st.find(s) == st.end()) {
                result.push_back(temp);
                st.insert(s);
            }
            return;
        }
        
        
        for(int i = 0; i < N; i++) {
            if(used[i] == false) {
                temp.push_back(arr[i]);
                used[i] = true;
                
                solve(arr, temp, used);
                
                used[i] = false;
                temp.pop_back();
            }
        }
    }
    
    vector<vector<int>> uniquePerms(vector<int> &arr ,int n) {
        N = n;
        
        vector<bool> used(n, false);
        vector<int> temp;
        sort(begin(arr), end(arr));
        solve(arr, temp, used);
        
        return result;
    }
};


```
