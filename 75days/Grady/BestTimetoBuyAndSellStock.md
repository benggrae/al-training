# Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

> 요약 주식의 차액을 구한다.

```text
  Example 1:

  Input: prices = [7,1,5,3,6,4]
  Output: 5
  Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
  Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
  Example 2:

  Input: prices = [7,6,4,3,1]
  Output: 0
  Explanation: In this case, no transactions are done and the max profit = 0.
  

  Constraints:

  1 <= prices.length <= 105
  0 <= prices[i] <= 104
  Accepted
  2,523,947
  Submissions

```

## 접근 방법

* 1번 케이스: 하나씩 다 구한다
* 2번 케이스: 한번 순회로 최저값과 최고값을 구한다.

```javascript
var maxProfit = function(prices) {
  let result = 0;
  for (let i = 0; i < prices.length - 1; i++){
    for (let j = i + 1; j < prices.length; j++) {
            const val = prices[j] - prices[i]
            if (result < val) {
                result = val
        }
    }
  }
  return result < 0 ? 0 : result
}
```

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    

        let minprice = Number.MAX_VALUE;
        let maxprofit = 0;
        for (let i = 0; i < prices.length; i++) {
            if (prices[i] < minprice)
                minprice = prices[i];
            else if (prices[i] - minprice > maxprofit)
                maxprofit = prices[i] - minprice;
        }
        return maxprofit;
};
```
