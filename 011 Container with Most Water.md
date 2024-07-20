# Container With Most Water :-

[Problem Link] :--- (https://leetcode.com/problems/container-with-most-water/description/)

<h3>
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).<br><br>

Find two lines that together with the x-axis form a container, such that the container contains the most water.<br><br>

Return the maximum amount of water a container can store.<br><br>

Notice that you may not slant the container.<br><br>

Example 1:<br>
Input: height = [1,8,6,2,5,4,8,3,7]<br>
Output: 49<br>
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.<br><br>

Example 2:<br>
Input: height = [1,1]<br>
Output: 1<br><br>

Constraints:<br><br>
n == height.length<br>
2 <= n <= 105<br>
0 <= height[i] <= 104<br>
  
</h3>

***Solution***

```

class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxArea = 0;
        int left = 0;
        int right = height.size() - 1;

        while (left < right) {
            maxArea = max(maxArea, (right - left) * min(height[left], height[right]));

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;        
    }
};

```
