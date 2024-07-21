# Maximum Points You Can Obtain from Cards :-

[Problem Link] :--- (https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/)

<h3>
There are several cards arranged in a row, and each card has an associated number of points. The points are given in the integer array cardPoints.<br><br>

In one step, you can take one card from the beginning or from the end of the row. You have to take exactly k cards.<br><br>

Your score is the sum of the points of the cards you have taken.<br><br>

Given the integer array cardPoints and the integer k, return the maximum score you can obtain.<br><br>

Example 1:<br>
Input: cardPoints = [1,2,3,4,5,6,1], k = 3<br>
Output: 12<br>
Explanation: After the first step, your score will always be 1. However, choosing the rightmost card first will maximize your total score. The optimal strategy is to take the three cards on the right, giving a final score of 1 + 6 + 5 = 12.<br><br>

Example 2:
I<br>nput: cardPoints = [2,2,2], k = 2<br>
Output: 4<br>
Explanation: Regardless of which two cards you take, your score will always be 4.<br><br>

Example 3:<br>
Input: cardPoints = [9,7,7,9,7,7,9], k = 7<br>
Output: 55<br>
Explanation: You have to take all the cards. Your score is the sum of points of all cards.<br><br>

Constraints:<br><br>
1 <= cardPoints.length <= 105<br>
1 <= cardPoints[i] <= 104<br>
1 <= k <= cardPoints.length<br>
  
</h3>

***Solution***

```

class Solution {
public:
    int maxScore(vector<int>& cardPoints, int k) {
        int res = 0;
        for(int i = 0 ; i<k ; i++)
        {
            res +=cardPoints[i];
        }
        int curr = res;
        for ( int i = k-1 ; i>=0 ; i--)
        {
            curr -= cardPoints[i];
            curr += cardPoints[cardPoints.size()-k+i];
            res = max(res , curr);
        }
        return res;
    }
};

```
