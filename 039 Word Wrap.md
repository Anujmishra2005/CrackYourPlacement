# Word Wrap :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/word-wrap1646/1)

<h3>
Given an array nums[] of size n, where nums[i] denotes the number of characters in one word. Let K be the limit on the number of characters that can be put in one line (line width). Put line breaks in the given sequence such that the lines are printed neatly.
Assume that the length of each word is smaller than the line width. When line breaks are inserted there is a possibility that extra spaces are present in each line. The extra spaces include spaces put at the end of every line except the last one. 
<br><br>
You have to minimize the following total cost where total cost = Sum of cost of all lines, where cost of line is = (Number of extra spaces in the line)2.<br><br>

Example 1:
Input: nums = {3,2,2,5}, k = 6
Output: 10
Explanation: Given a line can have 6
characters,
Line number 1: From word no. 1 to 1
Line number 2: From word no. 2 to 3
Line number 3: From word no. 4 to 4
So total cost = (6-3)2 + (6-2-2-1)2 = 32+12 = 10.
As in the first line word length = 3 thus
extra spaces = 6 - 3 = 3 and in the second line
there are two word of length 2 and there already
1 space between two word thus extra spaces
= 6 - 2 -2 -1 = 1. As mentioned in the problem
description there will be no extra spaces in
the last line. Placing first and second word
in first line and third word on second line
would take a cost of 02 + 42 = 16 (zero spaces
on first line and 6-2 = 4 spaces on second),
which isn't the minimum possible cost.<br><br>
Example 2:

Input: nums = {3,2,2}, k = 4
Output: 5
Explanation: Given a line can have 4 
characters,
Line number 1: From word no. 1 to 1
Line number 2: From word no. 2 to 2
Line number 3: From word no. 3 to 3
Same explaination as above total cost
= (4 - 3)2 + (4 - 2)2 = 5.<br>
 
Your Task:<br>
You don't need to read or print anyhting. Your task is to complete the function solveWordWrap() which takes nums and k as input paramater and returns the minimized total cost.<br>
 
Expected Time Complexity: O(n2)<br>
Expected Space Complexity: O(n)<br><br>
 

Constraints:<br><br>
1 ≤ n ≤ 500<br>
1 ≤ nums[i] ≤ 1000<br>
max(nums[i]) ≤ k ≤ 2000<br>
  
</h3>

***Solution***

```
class Solution {
public:
int n;
int solve(vector<int>&nums,int k,int idx,vector<int>&dp)
{
    if(idx>=n)
    {
        return 0;
    }
    if(dp[idx]!=-1)
    {
        return dp[idx];
    }
    int ans=INT_MAX;
    int sum=0;
    for(int i=idx;i<n;i++)
    {
        sum+=nums[i];
        if(k>=sum && i==n-1)
        {  
           ans=min(ans,solve(nums,k,i+1,dp)); 
        }
        else if(k>=sum)
        {  int x=k-sum;
           x=x*x;
           ans=min(ans,x+solve(nums,k,i+1,dp)); 
        }
        ++sum;
    }
    return dp[idx]=ans;
}
    int solveWordWrap(vector<int>nums, int k) 
    { 
        // Code here
        n=nums.size();
        vector<int>dp(n,-1);
        return solve(nums,k,0,dp);
    } 
};

```
