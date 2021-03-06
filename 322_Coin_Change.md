Medium

You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

Example 1:  
coins = [1, 2, 5], amount = 11  
return 3 (11 = 5 + 5 + 1)  

Example 2:  
coins = [2], amount = 3  
return -1.  

Note:  
You may assume that you have an infinite number of each kind of coin.

Solution v1(cpp):  
```cpp

# include <limits>

class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int *ans = new int[amount]();
        for (int i=0; i<amount; ++i) {
            ans[i] = std::numeric_limits<int>::max();
        }
        
        for (int i=0; i<coins.size(); ++i) {
            if (coins[i]<=amount) {
                ans[coins[i]-1] = 1;
            }
        }
        
        for (int i=0; i<amount; ++i) {
            for (int j=0; j<coins.size(); ++j) {
                if (coins[j]<i+1) {
                    if ((ans[i-coins[j]]!=std::numeric_limits<int>::max())&&(ans[i]>(ans[i-coins[j]]+1))) {
                        ans[i] = ans[i-coins[j]] + 1;
                    }   // INT_MAX + 1 = INT_MIN
                }
            }
        }

        if (ans[amount-1] == std::numeric_limits<int>::max()) return -1;
        return ans[amount-1];
   }
};
```
