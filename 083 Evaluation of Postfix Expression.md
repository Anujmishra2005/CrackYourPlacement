#  Evaluation of Postfix Expression :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/evaluation-of-postfix-expression1735/1)

<h3>
Given string S representing a postfix expression, the task is to evaluate the expression and find the final value. Operators will only include the basic arithmetic operators like *, /, + and -.<br><br>

Example 1:<br>
Input: S = "231*+9-"<br>
Output: -4<br>
Explanation:<br>
After solving the given expression,<br>
we have -4 as result.<br><br>
Example 2:<br>
Input: S = "123+*8-"<br>
Output: -3<br>
Explanation:<br>
After solving the given postfix <br>
expression, we have -3 as result.<br><br>

Your Task:<br><br>
You do not need to read input or print anything. Complete the function evaluatePostfixExpression() that takes the string S denoting the expression as input parameter and returns the evaluated value.<br><br>


Expected Time Complexity: O(|S|)<br>
Expected Auixilliary Space: O(|S|)<br><br>


Constraints:<br><br>
1 ≤ |S| ≤ 105<br>

0 ≤ |Si|≤ 9 (And given operators)<br><br>
  
</h3>

***Solution***

```

class Solution
{
    public:
    //Function to evaluate a postfix expression.
    int evaluatePostfix(string S)
    {
        // Your code here
        stack<int>sta;
        int n=S.length();
        for(int i=0;i<n;i++)
        {
            if(S[i]!='*'&&S[i]!='/'&& S[i]!='+' && S[i]!='-')
            sta.push(S[i]-'0');//convert char to int and then push
            else
            {
                int a = sta.top();
                sta.pop();
                int b = sta.top();
                sta.pop();
                int temp ;
                if(S[i]=='+')
                temp = b+a;
                else if(S[i]=='-')
                 temp = b-a;
                else if(S[i]=='*')
                 temp = b*a;
                 else
                 temp =b/a;
                sta.push(temp);
            }
        }
        return sta.top();
    }
};

```
