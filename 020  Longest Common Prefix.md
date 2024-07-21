# Longest Common Prefix :-

[Problem Link] :--- (https://leetcode.com/problems/longest-common-prefix/description/)

<h3>
Write a function to find the longest common prefix string amongst an array of strings.<br><br>

If there is no common prefix, return an empty string "".<br><br>

Example 1:<br>
Input: strs = ["flower","flow","flight"]<br>
Output: "fl"<br>

Example 2:<br>
Input: strs = ["dog","racecar","car"]<br>
Output: ""<br>
Explanation: There is no common prefix among the input strings.<br><br>
 
Constraints:<br>
1 <= strs.length <= 200<br>
0 <= strs[i].length <= 200<br>
strs[i] consists of only lowercase English letters.<br><br>
  
</h3>

***Solution***

```
class Solution {
public:
    string longestCommonPrefix(vector<string>& v) {
        string ans="";
        sort(v.begin(),v.end());
        int n=v.size();
        string first=v[0],last=v[n-1];
        for(int i=0;i<min(first.size(),last.size());i++){
            if(first[i]!=last[i]){
                return ans;
            }
            ans+=first[i];
        }
        return ans;
    }
};

```
