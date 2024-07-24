# Add Binary :-

[Problem Link] :--- (https://leetcode.com/problems/add-binary/description/)

<h3>
Given two binary strings a and b, return their sum as a binary string.<br><br>

Example 1:<br>
Input: a = "11", b = "1"<br>
Output: "100"<br><br>
Example 2:<br>
Input: a = "1010", b = "1011"<br>
Output: "10101"<br><br>

Constraints:<br>
1 <= a.length, b.length <= 104<br>
a and b consist only of '0' or '1' characters.<br>
Each string does not contain leading zeros except for the zero itself.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    string addBinary(string a, string b) {
        string res;
        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;
        while(i >= 0 || j >= 0){
            int sum = carry;
            if(i >= 0) sum += a[i--] - '0';
            if(j >= 0) sum += b[j--] - '0';
            carry = sum > 1 ? 1 : 0;
            res += to_string(sum % 2);
        }
        if(carry) res += to_string(carry);
        reverse(res.begin(), res.end());
        return res;
    }
};

```
