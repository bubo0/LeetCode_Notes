Description:

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

**Notes: 

1 size ***n*** problem -> create size ***n+1*** space to solve it may simplify the solution under special conditions

2 pay attention to the indices especially when there are multiple dimensions. Double check to make sure that the variable i and j etc. are in the right position.


My Solution:

```java

class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        if (0==m||0==n) return 0;
        
        int[] num = new int[m+1];
        
        num[0] = 0;
        if (1==obstacleGrid[0][0]) return 0;
        num[1] = 1;
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                if (1==obstacleGrid[j][i]) num[j+1] = 0;   //!!! pay attention to the index! especially when there are multple dimensions!
                else num[j+1] = num[j] + num[j+1];
            }    
        }
        return num[m];
        /*
        for (int i=0; i<m; ++i) {
            if (1==obstacleGrid[i][0]) {
                num[i] = 0;
                break;
            }
            else num[i] = 1;
        }
        
        if (1==n) return num[m-1];
        
        if (1==m) {
            
            // get wrong when the input is [[0,1]]:
            for (int l=0; l<n; ++l) {  // 1  start from 0 instead of 1 !!!  2  bug fixed: ++l instead of ++n !!!
                if (1==obstacleGrid[0][l]) return 0;
            }
            return 1;
        }
        else {
        for (int j=1; j<n; ++j) {
            for (int k=1; k<m; ++k) {
                if (1==obstacleGrid[k][j]) num[k] = 0;
                else num[k] = num[k] + num[k-1];
            }
        }
        return num[m-1];
        
        }
        
        */

    }
}

```
