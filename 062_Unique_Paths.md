**Description**

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

**Notes**


**My Solution**

**Time & Space Complexity**
O(m)(n); O(m) (or O(n))

```java
class Solution {
    public int uniquePaths(int m, int n) {
        if (0>=m||0>=n) return 0;
        
        int[] num = new int[m];
        for (int i=0; i<m; ++i) num[i] = 1;
        for (int j=1; j<n; ++j) {
            for (int k=1; k<m; ++k) {
                num[k] = num[k] + num[k-1];
            }
        }
        return num[m-1];
    }
}
```

