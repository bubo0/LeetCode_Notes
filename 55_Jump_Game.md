Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

Solution
----

**Time Complexity**  
O(n)
**Space Complexity**  
O(n)

```java
/* My solution (too slow)

class Solution {
    public boolean canJump(int[] nums) {
        if (0==nums.length) return false;
        
        // Attention: it should be boolean instead of bool in java
        boolean[] can = new boolean[nums.length];
        can[0] = true;
        for (int i=0; i<nums.length; ++i) {
            if (true==can[i]) {
                for (int j=1; (j<nums[i]+1)&&((i+j)<nums.length); ++j) {
                    can[i+j] = true;
                }
            }
        }
        
        // carelessness: num[] vs can[]
        return can[nums.length-1];
    } 
}

*/

/*
    fastest solution example

    1. from n to 1 instead of from 1 to n
    2. simplify the judgement of for
    3. do calculation in return -> easier to understand
*/

class Solution {
  public boolean canJump(int[] nums) {
    int leftMostGoodPosition = nums.length - 1;
    for (int i = nums.length - 1; i >= 0; i--) {
      if (i + nums[i] >= leftMostGoodPosition) {
        leftMostGoodPosition = i;
      }
    }
    
    return leftMostGoodPosition == 0;
  }
}

```
