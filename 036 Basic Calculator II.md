# Basic Calculator II :-

[Problem Link] :--- (https://leetcode.com/problems/basic-calculator-ii/description/)

<h3>
Given a string s which represents an expression, evaluate this expression and return its value. <br>
The integer division should truncate toward zero.<br>
You may assume that the given expression is always valid. All intermediate results will be in the range of [-231, 231 - 1].<br>
Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().<br><br>

Example 1:<br>
Input: s = "3+2*2"<br>
Output: 7<br><br>
Example 2:<br>
Input: s = " 3/2 "<br>
Output: 1<br><br>
Example 3:<br>
Input: s = " 3+5 / 2 "<br>
Output: 5<br>
 
Constraints:<br>
1 <= s.length <= 3 * 105<br>
s consists of integers and operators ('+', '-', '*', '/') separated by some number of spaces.<br>
s represents a valid expression.<br>
All the integers in the expression are non-negative integers in the range [0, 231 - 1].<br>
The answer is guaranteed to fit in a 32-bit integer.<br>
  
</h3>

***Solution***

```

class Solution {
public:
    string toPostfix(string& s) {
        auto precedence = [](char c){return c == '*' || c == '/';};
        stack<char> op;
        string post = "";
        for(auto c : s) 
            if(c == ' ') continue;
            else if(isdigit(c)) post += c;
            else {
                post += '|';                              // markers to separate numbers
                while(size(op) && precedence(c) <= precedence(op.top())) 
                    post += op.top(), op.pop();
                op.push(c);
            }
        
        post += '|';
        while(size(op)) 
            post += op.top(), op.pop();        
        return post;
    }
    int calculate(string& s) {
        s = toPostfix(s);
        stack<int> num;
        for(int i = 0; i < size(s); i++) 
            if(isdigit(s[i])) {
                int cur = 0;
                while(i < size(s) && isdigit(s[i]))
                    cur = cur * 10 + (s[i++] - '0');
                num.push(cur);
            }
            else {
                int num1 = num.top(); num.pop();
                int num2 = num.top(); num.pop();
                if(s[i] == '*')      num.push(num2 * num1);
                else if(s[i] == '/') num.push(num2 / num1);
                else if(s[i] == '+') num.push(num2 + num1);
                else if(s[i] == '-') num.push(num2 - num1);
            }
        
        return num.top();
    }
};

```
