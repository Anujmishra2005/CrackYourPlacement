# Valid Number :-

[Problem Link] :--- (https://leetcode.com/problems/valid-number/description/)

<h3>
Given a string s, return whether s is a valid number.
<br>
For example, all the following are valid numbers: "2", "0089", "-0.1", "+3.14", "4.", "-.9", "2e10", "-90E3", "3e+7", "+6e-1", "53.5e93", "-123.456e789", while the following are not valid numbers: "abc", "1a", "1e", "e3", "99e2.5", "--6", "-+3", "95a54e53".
<br>
Formally, a valid number is defined using one of the following definitions:
<br>
An integer number followed by an optional exponent.<br>
A decimal number followed by an optional exponent.<br>
An integer number is defined with an optional sign '-' or '+' followed by digits.<br>
<br>
A decimal number is defined with an optional sign '-' or '+' followed by one of the following definitions:<br>

Digits followed by a dot '.'.<br>
Digits followed by a dot '.' followed by digits.<br>
A dot '.' followed by digits.<br>
An exponent is defined with an exponent notation 'e' or 'E' followed by an integer number.<br>

The digits are defined as one or more digits.<br><br>

Example 1:<br>

Input: s = "0"<br>

Output: true<br><br>

Example 2:<br>

Input: s = "e"<br>

Output: false<br><br>

Example 3:<br>

Input: s = "."<br>

Output: false<br>
 
Constraints:<br><br>
1 <= s.length <= 20<br>
s consists of only English letters (both uppercase and lowercase), digits (0-9), plus '+', minus '-', or dot '.'.<br>
  
</h3>

***Solution***

```

enum STATE {
    INIT, I1, I2, I3, I4, I5, S1, S2, S3
};

bool isNum(char ch) {
    return ch >= 48 && ch <= 57;
}

class Solution {
public:
    bool isTrueState(STATE s) {
        return s == S1 || s == S2 || s == S3;
    }

    bool isNumber(string s) {
        STATE curr = INIT;

        for (int i = 0; i < s.length(); i++) {
            if (curr == INIT && (s[i] == '+' || s[i] == '-')) {
                curr = I1;
            } else if (curr == INIT && isNum(s[i])) {
                curr = S1;
            } else if (curr == INIT && s[i] == '.') {
                curr = I2;
            } else if (curr == I1 && isNum(s[i])) {
                curr = S1;
            } else if (curr == I1 && s[i] == '.') {
                curr = I2;
            } else if (curr == S1 && (s[i] == 'e' || s[i] == 'E')) {
                curr = I3;
            } else if (curr == S1 && s[i] == '.') {
                curr = S2;
            } else if (curr == S1 && isNum(s[i])) {
                curr = S1;
            } else if (curr == I2 && isNum(s[i])) {
                curr = S2;
            } else if (curr == I3 && isNum(s[i])) {
                curr = S3;
            } else if (curr == I3 && (s[i] == '+' || s[i] == '-')) {
                curr = I5;
            } else if (curr == S2 && (s[i] == 'e' || s[i] == 'E')) {
                curr = I4;
            } else if (curr == S2 && isNum(s[i])) {
                curr = S2;
            } else if (curr == I4 && isNum(s[i])) {
                curr = S3;
            } else if (curr == I4 && (s[i] == '+' || s[i] == '-')) {
                curr = I5;
            } else if (curr == I5 && isNum(s[i])) {
                curr = S3;
            } else if (curr == S3 && isNum(s[i])) {
                curr = S3;
            } else {
                return false;
            }
        }

        return isTrueState(curr);
    }
};

```
