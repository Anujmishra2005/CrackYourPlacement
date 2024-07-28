# Minimum Swaps to Sort :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/minimum-swaps/1)

<h3>
Given an array of n distinct elements. Find the minimum number of swaps required to sort the array in strictly increasing order.<br><br>
Example 1:<br>
Input:<br>
nums = {2, 8, 5, 4}<br>
Output:<br>
1<br>
Explanation:<br>
swap 8 with 4.<br><br>
Example 2:<br>

Input:<br>
nums = {10, 19, 6, 3, 5}<br>
Output:<br>
2<br>
Explanation:<br>
swap 10 with 3 and swap 19 with 5.<br><br>

Your Task:<br>
You do not need to read input or print anything. Your task is to complete the function minSwaps() which takes the nums as input parameter and returns an integer denoting the minimum number of swaps required to sort the array.
If the array is already sorted, return 0. <br><br>


Expected Time Complexity: O(nlogn)<br>
Expected Auxiliary Space: O(n)<br>
 
Constraints:<br><br>
1 ≤ n ≤ 105<br>
1 ≤ numsi ≤ 106<br>
  
</h3>

***Solution***

```

class Solution 
{
    public:
    //Function to find the minimum number of swaps required to sort the array. 
    int minSwaps(vector<int>&nums)
    {
        vector<int>ans;
        int n=nums.size();
      unordered_map<int ,int>s;
      for(int i=0;i<n;i++){
          s.insert({nums[i],i});
          ans.push_back(nums[i]);
      }
      int count=0;
      sort(nums.begin(),nums.end());
      for(int i=0;i<n;i++){
          if(nums[i]!=ans[i]){
              int i1=s[nums[i]];
              int i2=s[ans[i]];
              swap(ans[i1],ans[i2]);
              s[ans[i1]]=i1;
              s[ans[i2]]=i2;
              count++;
              
          }
      }
      return count;
    }
};

```
