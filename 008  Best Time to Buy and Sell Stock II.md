# Best Time to Buy and Sell Stock II :-

[Problem Link] :--- (https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)

<h3>
You are given an integer array prices where prices[i] is the price of a given stock on the ith day.<br><br>

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.<br><br>

Find and return the maximum profit you can achieve.<br><br>

Example 1:<br>
Input: prices = [7,1,5,3,6,4]<br>
Output: 7<br>
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.<br>
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.<br>
Total profit is 4 + 3 = 7.<br><br>

Example 2:<br>
Input: prices = [1,2,3,4,5]<br>
Output: 4<br>
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.<br>
Total profit is 4.<br><br>

Example 3:<br>
Input: prices = [7,6,4,3,1]<br>
Output: 0<br>
Explanation: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.<br><br>
 
Constraints:<br>
1 <= prices.length <= 3 * 104<br>
0 <= prices[i] <= 104<br>
  
</h3>

***Solution***

```

#include<bits/stdc++.h>
using namespace std;

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit = 0;
        for(int i=1;i<prices.size();i++)
        {
            if(prices[i]>prices[i-1])
            {
                profit = profit + (prices[i]-prices[i-1]);
            }
        }
        return profit;
    }

};

```
