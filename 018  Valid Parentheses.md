# Valid Parentheses :-

[Problem Link] :--- (https://leetcode.com/problems/valid-parentheses/description/)

<h3>
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.<br><br>

An input string is valid if:<br><br>

Open brackets must be closed by the same type of brackets.<br><br>
Open brackets must be closed in the correct order.<br><br>
Every close bracket has a corresponding open bracket of the same type.<br><br>

Example 1:<br>
Input: s = "()"<br>
Output: true<br><br>

Example 2:<br>
Input: s = "()[]{}"<br>
Output: true<br><br>

Example 3:<br>
Input: s = "(]"<br>
Output: false<br><br>
 
Constraints:<br>
1 <= s.length <= 104<br>
s consists of parentheses only '()[]{}'.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isValid(string s) {
        stack<char>st;
        for(char c : s){
            if(c =='(' || c == '{' || c =='['){
                st.push(c);
            }else{
                if (st.empty() || 
                (c == ')' && st.top()!= '(') || 
                (c == '}' && st.top()!='{') ||
                (c == ']' && st.top()!='[')){
                    return false;
                }
                st.pop();
            }
        }
        return st.empty();
    }
};

```
