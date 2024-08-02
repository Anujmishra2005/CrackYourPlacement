# Remove All Adjacent Duplicates in String II :-

[Problem Link] :--- (https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/description/)

<h3>
You are given a string s and an integer k, a k duplicate removal consists of choosing k adjacent and equal letters from s and removing them, causing the left and the right side of the deleted substring to concatenate together.
<br>
We repeatedly make k duplicate removals on s until we no longer can.<br>

Return the final string after all such duplicate removals have been made. It is guaranteed that the answer is unique.<br><br>

Example 1:<br>
Input: s = "abcd", k = 2<br>
Output: "abcd"<br>
Explanation: There's nothing to delete.<br><br>
Example 2:<br>

Input: s = "deeedbbcccbdaa", k = 3<br>
Output: "aa"<br>
Explanation: <br>
First delete "eee" and "ccc", get "ddbbbdaa"
Then delete "bbb", get "dddaa"
Finally delete "ddd", get "aa"<br><br>
Example 3:<br>

Input: s = "pbbcggttciiippooaais", k = 2<br>
Output: "ps"<br><br>
 

Constraints:<br><br>

1 <= s.length <= 105<br>
2 <= k <= 104<br>
s only contains lowercase English letters.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    string removeDuplicates(string s, int k) {
        stack<pair<char, int>> st;
        for(int i = 0; i<s.size(); ++i){
            if(!st.empty() && st.top().first == s[i]){
                pair<char, int> temp = st.top();
                st.pop();
                if(temp.second < k - 1) st.push({temp.first, temp.second + 1});
            }
            else st.push({s[i], 1});
        }
        string res;
        while(!st.empty()){
            while(st.top().second--)
                res += st.top().first;
            st.pop();
        }
        reverse(res.begin(), res.end());
        return res;
    }
};

```
