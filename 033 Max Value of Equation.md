# Max Value of Equation :-

[Problem Link] :--- (https://leetcode.com/problems/max-value-of-equation/description/)

<h3>
You are given an array points containing the coordinates of points on a 2D plane, sorted by the x-values, where points[i] = [xi, yi] such that xi < xj for all 1 <= i < j <= points.length. You are also given an integer k.<br><br>
Return the maximum value of the equation yi + yj + |xi - xj| where |xi - xj| <= k and 1 <= i < j <= points.length.<br><br>
It is guaranteed that there exists at least one pair of points that satisfy the constraint |xi - xj| <= k.<br><br>


Example 1:<br>
Input: points = [[1,3],[2,0],[5,10],[6,-10]], k = 1<br>
Output: 4<br>
Explanation: The first two points satisfy the condition |xi - xj| <= 1 and if we calculate the equation we get 3 + 0 + |1 - 2| = 4. Third and fourth points also satisfy the condition and give a value of 10 + -10 + |5 - 6| = 1.<br>
No other pairs satisfy the condition, so we return the max of 4 and 1.<br><br>
Example 2:<br>
Input: points = [[0,0],[3,0],[9,2]], k = 3<br>
Output: 3<br>
Explanation: Only the first two points have an absolute difference of 3 or less in the x-values, and give the value of 0 + 0 + |0 - 3| = 3.<br><br>




Constraints:<br><br>
2 <= points.length <= 105<br>
points[i].length == 2<br>
-108 <= xi, yi <= 108<br>
0 <= k <= 2 * 108<br>
xi < xj for all 1 <= i < j <= points.length<br>
xi form a strictly increasing sequence.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int findMaxValueOfEquation(vector<vector<int>>& v, int k) {
        priority_queue<vector<int>> pq;
        pq.push({v[0][1]-v[0][0],v[0][0]});
        int ans = INT_MIN,sum;
        for(int i = 1; i < v.size(); i++){
            sum = v[i][0]+v[i][1];
            while(!pq.empty() && v[i][0]-pq.top()[1]>k)pq.pop();
            if(!pq.empty()){
                ans = max(ans,sum+pq.top()[0]);
            }
            pq.push({v[i][1]-v[i][0],v[i][0]});
        }
        return ans;
    }
};

```
