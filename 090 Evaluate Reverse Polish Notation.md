# Evaluate Reverse Polish Notation :-

[Problem Link] :--- (https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)

<h3>
You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.
<br>
Evaluate the expression. Return an integer that represents the value of the expression.
<br><br>
Note that:<br><br>

The valid operators are '+', '-', '*', and '/'.<br>
Each operand may be an integer or another expression.<br>
The division between two integers always truncates toward zero.<br>
There will not be any division by zero.<br>
The input represents a valid arithmetic expression in a reverse polish notation.<br>
The answer and all the intermediate calculations can be represented in a 32-bit integer.<br><br><br>

Example 1:<br>
Input: tokens = ["2","1","+","3","*"]<br>
Output: 9<br>
Explanation: ((2 + 1) * 3) = 9<br><br>
Example 2:<br>

Input: tokens = ["4","13","5","/","+"]<br>
Output: 6<br>
Explanation: (4 + (13 / 5)) = 6<br><br>
Example 3:<br>

Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]<br>
Output: 22<br>
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5<br>
= ((10 * (6 / (12 * -11))) + 17) + 5<br>
= ((10 * (6 / -132)) + 17) + 5<br>
= ((10 * 0) + 17) + 5<br>
= (0 + 17) + 5<br>
= 17 + 5<br>
= 22<br><br>
 

Constraints:<br><br>

1 <= tokens.length <= 104<br>
tokens[i] is either an operator: "+", "-", "*", or "/", or an integer in the range [-200, 200].<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> stack;
        for (const string& token : tokens) {
            if (isdigit(token.back())) {
                stack.push(stoi(token));
            } else {
                int val2 = stack.top();
                stack.pop();
                int val1 = stack.top();
                stack.pop();
                int result;
                switch (token[0]) {
                    case '*':
                        result = val1 * val2;
                        break;
                    case '+':
                        result = val1 + val2;
                        break;
                    case '-':
                        result = val1 - val2;
                        break;
                    case '/':
                        result = val1 / val2;
                        break;
                }
                stack.push(result);
            }
        }
        return stack.top();
    }
};

```
