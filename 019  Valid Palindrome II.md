# Valid Palindrome II :-

[Problem Link] :--- (https://leetcode.com/problems/valid-palindrome-ii/description/)

<h3>
Given a string s, return true if the s can be palindrome after deleting at most one character from it.<br><br>

Example 1:<br>
Input: s = "aba"<br>
Output: true<br><br>

Example 2:<br>
Input: s = "abca"<br>
Output: true<br>
Explanation: You could delete the character 'c'.<br><br>

Example 3:<br>
Input: s = "abc"<br>
Output: false<br><br>
 
Constraints:<br>
1 <= s.length <= 105<br>
s consists of lowercase English letters.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool validPalindrome(string s) {
        int i = 0;
        int j = s.size()-1;
        while (i <= j)
        {
            if(s[i] == s[j])
            {
                i++;
                j--;
            }
            else{
                return isPalindrome(s,i+1,j) || isPalindrome(s,i,j-1);
            }
        }
        return true;
    }
    bool isPalindrome(string s , int i , int j)
    {
        while ( i <= j)
        {
            if ( s[i] == s[j])
            {
                i++;
                j--;
            }
            else{
                return false;
            }
        }
        return true;
    }
};

```
