# Stock buy sell

**CODE**
```cpp

#include <vector>

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxProfit = 0;
        int size = prices.size();
        int k = 0; // Index of the buying day
        int i = 1; // Index of the selling day

        while (i < size) {
            int profit = prices[i] - prices[k];

            if (profit <= 0) {
                k =i;
            } else if (profit >= maxProfit) {
                maxProfit = profit;
            }
            
            i++;
        }
        
        return maxProfit;
    }
};
```
