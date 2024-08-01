# Daily Temperatures :-

[Problem Link] :--- (https://leetcode.com/problems/daily-temperatures/description/)

<h3>
Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.<br><br>

Example 1:<br>
Input: temperatures = [73,74,75,71,69,72,76,73]<br>
Output: [1,1,4,2,1,1,0,0]<br><br>
Example 2:<br>

Input: temperatures = [30,40,50,60]<br>
Output: [1,1,1,0]<br><br>
Example 3:<br>

Input: temperatures = [30,60,90]<br>
Output: [1,1,0]<br><br>
 

Constraints:<br><br>

1 <= temperatures.length <= 105<br>
30 <= temperatures[i] <= 100<br><br>
  
</h3>

***Solution***

```


class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        int n = temperatures.size();
        vector<int> answer(n, 0);
        stack<int> s; // Stack to store the indices
        for(int i = 0; i < n;i++){
            while(!s.empty() && temperatures[i] > temperatures[s.top()]){
                int idx = s.top();
                s.pop();
                answer[idx] = i - idx; 
            }
            s.push(i); 
        }

        return answer;
    }
};

```
