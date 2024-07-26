# Distinct Subsequences :-

[Problem Link] :--- (https://leetcode.com/problems/distinct-subsequences/description/)

<h3>
Given two strings s and t, return the number of distinct subsequences of s which equals t.
<br><br>
The test cases are generated so that the answer fits on a 32-bit signed integer.<br><br>

Example 1:<br>
Input: s = "rabbbit", t = "rabbit"<br>
Output: 3<br>
Explanation:<br>
As shown below, there are 3 ways you can generate "rabbit" from s.<br>
rabbbit<br>
rabbbit<br>
rabbbit<br><br>
Example 2:<br>
Input: s = "babgbag", t = "bag"<br>
Output: 5<br>
Explanation:<br>
As shown below, there are 5 ways you can generate "bag" from s.<br>
babgbag<br>
babgbag<br>
babgbag<br>
babgbag<br>
babgbag<br><br>
 
Constraints:<br><br>
1 <= s.length, t.length <= 1000<br>
s and t consist of English letters.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int dp[1001][1001];
    int solve(int currentInd, int currentTarIn, string &s, string &t) {
      if(currentTarIn >= (t.size())) {
        return 1;
      }
      if(currentInd>=(s.size())) {
        return 0;
      }
      if(dp[currentInd][currentTarIn] != -1) {
        return dp[currentInd][currentTarIn];
      }
      int res1 = solve(currentInd + 1, currentTarIn, s, t);
      if(s[currentInd] == t[currentTarIn]) {
        res1 += solve(currentInd + 1, currentTarIn + 1, s, t);
      }
      return dp[currentInd][currentTarIn] = res1;
    }
    int numDistinct(string s, string t) {
        memset(dp, -1, sizeof(dp));
        return solve(0, 0, s, t);
    }
};

```
