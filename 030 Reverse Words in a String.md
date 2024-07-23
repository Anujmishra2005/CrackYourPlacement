# Reverse Words in a String :-

[Problem Link] :--- (https://leetcode.com/problems/reverse-words-in-a-string/description/)

<h3>
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.<br><br>
Return a string of the words in reverse order concatenated by a single space.<br><br>
Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.<br><br>

Example 1:<br>
Input: s = "the sky is blue"<br>
Output: "blue is sky the"<br><br>
Example 2:<br>
Input: s = "  hello world  "<br>
Output: "world hello"<br>
Explanation: Your reversed string should not contain leading or trailing spaces.<br><br>
Example 3:<br>
Input: s = "a good   example"<br>
Output: "example good a"<br>
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.<br><br>
 
Constraints:<br><br>
1 <= s.length <= 104<br>
s contains English letters (upper-case and lower-case), digits, and spaces ' '.<br>
There is at least one word in s.<br><br>

Follow-up: If the string data type is mutable in your language, can you solve it in-place with O(1) extra space?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    string reverseWords(string s) {
        reverse(s.begin(), s.end());
        int n = s.size();
        int left = 0;
        int right = 0;
        int i = 0;
        while (i < n) {
            while (i < n && s[i] == ' ')
                i++;
            if (i == n)
                break;
            while (i < n && s[i] != ' ') {
                s[right++] = s[i++];
            }
            reverse(s.begin() + left, s.begin() + right);
            s[right++] = ' ';
            left = right;
            i++;
        }
        s.resize(right - 1);
        return s;
    }
};

```
