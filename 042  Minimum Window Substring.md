# Minimum Window Substring :-

[Problem Link] :--- (https://leetcode.com/problems/minimum-window-substring/description/)

<h3>
Given two strings s and t of lengths m and n respectively, return the minimum window
substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".<br>
The testcases will be generated such that the answer is unique.<br><br>

Example 1:<br>
Input: s = "ADOBECODEBANC", t = "ABC"<br>
Output: "BANC"<br>
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.<br><br>
Example 2:<br>

Input: s = "a", t = "a"<br>
Output: "a"<br>
Explanation: The entire string s is the minimum window.<br><br>
Example 3:<br>

Input: s = "a", t = "aa"<br>
Output: ""<br>
Explanation: Both 'a's from t must be included in the window.<br>
Since the largest window of s only has one 'a', return empty string.<br><br>
 
Constraints:<br><br>
m == s.length<br>
n == t.length<br>
1 <= m, n <= 105<br>
s and t consist of uppercase and lowercase English letters.<br>
Follow up: Could you find an algorithm that runs in O(m + n) time?<br>
  
</h3>

***Solution***

```

class Solution {
public:
    string minWindow(string s, string t) {
        if (s.length() < t.length()) return "";
        
        vector<int> map(128, 0);
        int count = t.length();
        int start = 0, minStart = 0, minLen = INT_MAX;
        
        for (char c : t) map[c]++;
        
        for (int end = 0; end < s.length(); end++) {
            if (map[s[end]]-- > 0) count--;
            
            while (count == 0) {
                if (end - start + 1 < minLen) {
                    minStart = start;
                    minLen = end - start + 1;
                }
                
                if (map[s[start++]]++ == 0) count++;
            }
        }
        
        return minLen == INT_MAX ? "" : s.substr(minStart, minLen);
    }
};

```
