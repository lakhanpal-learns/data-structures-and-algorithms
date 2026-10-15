# 121. Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

## Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
Example 2:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.

## observation 
>find the lowest day price then higest  
> search depend on the time 
> check the search are not the last value which cause the erro 
> calucation then go 


## code 
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int lowest = INT_MAX;
        int highest = 0;

        for (int i = 0; i < prices.size(); i++) {
            lowest = min(lowest, prices[i]);

            int profit = prices[i] - lowest;
            highest = max(highest, profit);
        }

        return highest;
    }
};

## why my observaton go wrong 
Your observation went wrong because you focused on finding the lowest price in the entire array, instead of considering the order of buying and selling.

Your key lesson: Don't assume your observation is correct just because it works for one example. Try to disprove it with a tricky example before writing code.

Your observation goes wrong when you focus on one part of the problem without checking all the constraints and possible cases.

