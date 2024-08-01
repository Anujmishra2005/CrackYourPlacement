# Backspace String Compare :-

[Problem Link] :--- (https://leetcode.com/problems/backspace-string-compare/description/)

<h3>
Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.
<br><br>
Note that after backspacing an empty text, the text will continue empty.<br><br>

Example 1:<br>
Input: s = "ab#c", t = "ad#c"<br>
Output: true<br>
Explanation: Both s and t become "ac".<br><br>
Example 2:<br>
Input: s = "ab##", t = "c#d#"<br>
Output: true<br>
Explanation: Both s and t become "".<br><br>
Example 3:<br>
Input: s = "a#c", t = "b"<br>
Output: false<br>
Explanation: s becomes "c" while t becomes "b".<br><br>
 

Constraints:<br><br>
1 <= s.length, t.length <= 200<br>
s and t only contain lowercase letters and '#' characters.<br><br>
 

Follow up: Can you solve it in O(n) time and O(1) space?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool backspaceCompare(string s, string t) {
        stack<char> st;
        stack<char> p;
        
        for(int i = 0; i < s.size(); i++) {
            if(s[i] == '#') {
                if(!st.empty()) {
                    st.pop();
                }
            } else {
                st.push(s[i]);
            }
        }
        
        for(int i = 0; i < t.size(); i++) {
            if(t[i] == '#') {
                if(!p.empty()) {
                    p.pop();
                }
            } else {
                p.push(t[i]);
            }
        }
        
        while(!st.empty() && !p.empty()) {
            if(st.top() != p.top()) {
                return false;
            }
            st.pop();
            p.pop();
        }
        
        return st.empty() && p.empty();
    }
};

```
