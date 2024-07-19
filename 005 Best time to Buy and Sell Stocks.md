# Sort Colors :-

[Problem Link] :--- (https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

<h3>
You are given an array prices where prices[i] is the price of a given stock on the ith day.<br>

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.<br>

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.<br><br>

Example 1:<br>
Input: prices = [7,1,5,3,6,4]<br>
Output: 5<br>
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.<br>
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.<br><br>

Example 2:<br>
Input: prices = [7,6,4,3,1]<br>
Output: 0<br>
Explanation: In this case, no transactions are done and the max profit = 0.<br><br>
 
Constraints:<br>
1 <= prices.length <= 105<br>
0 <= prices[i] <= 104<br>
  
</h3>

***Solution***

```

#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buy = prices[0];
        int profit = 0;
        for (int i = 0; i < prices.size();i++)
        {
            if(prices[i] < buy)
            {
                buy = prices[i];
            }
            else if(profit < prices[i] - buy)
            {
                profit = prices[i] - buy;
            }
        }
        return profit;
    }
};

```
