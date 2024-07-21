# Find the Index of the First Occurrence in a String :-

[Problem Link] :--- (https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)

<h3>
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.<br><br>
  
Example 1:<br>
Input: haystack = "sadbutsad", needle = "sad"<br>
Output: 0<br>
Explanation: "sad" occurs at index 0 and 6.<br>
The first occurrence is at index 0, so we return 0.<br><br>

Example 2:<br>
Input: haystack = "leetcode", needle = "leeto"<br>
Output: -1<br>
Explanation: "leeto" did not occur in "leetcode", so we return -1.<br><br>
 
Constraints:<br>
1 <= haystack.length, needle.length <= 104<br>
haystack and needle consist of only lowercase English characters.<br><br>
  
</h3>

***Solution***

```
class Solution {
public:
    int strStr(string haystack, string needle) {
        int hLen = haystack.length();
        int nLen = needle.length();
        int nIndex = 0;
        for(int i=0; i<hLen; i++){
            if(haystack[i]==needle[nIndex]){
                nIndex++;
            }
            else{
                i=i-nIndex;
                nIndex=0;
            }
            if(nIndex==nLen){
                return i-nLen+1;
            }
        }
        return -1;
    }
};

```
