# Group Anagrams :-

[Problem Link] :--- (https://leetcode.com/problems/group-anagrams/description/)

<h3>
Given an array of strings strs, group the anagrams together. You can return the answer in any order.<br><br>
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.<br><br>

Example 1:<br>
Input: strs = ["eat","tea","tan","ate","nat","bat"]<br>
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]<br><br>
Example 2:<br>
Input: strs = [""]<br>
Output: [[""]]<br><br>
Example 3:<br>
Input: strs = ["a"]<br>
Output: [["a"]]<br><br>
 
Constraints:<br><br>
1 <= strs.length <= 104<br>
0 <= strs[i].length <= 100<br>
strs[i] consists of lowercase English letters.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string>> mp;
        
        for(auto x: strs){
            string word = x;
            sort(word.begin(), word.end());
            mp[word].push_back(x);
        }
        
        vector<vector<string>> ans;
        for(auto x: mp){
            ans.push_back(x.second);
        }
        return ans;
    }
};

```
