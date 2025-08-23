# 463. Island Perimeter

## Strategy:
 - iterate through matrix
 - find 1st island cell
 - use dfs
 - whenever you "step off" the island, increment the counter
 - return final count
 - instead of incrementing, return 1 if water and 0 if island and sum recursive calls
## Alternate Strategy:
 - iterate through matrix and add/subtract perimeter based on neighbors
 - likely leads to faster runtime

## Solution
```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        # iterate through matrix
        # find 1st island cell
        # use dfs
        # whenever you "step off" the island, increment the counter
        # return final count
        rows, cols = len(grid), len(grid[0])
        visited = [[False for _ in range(cols)] for _ in range(rows)]
        def dfs(i, j):
            if i < 0 or i > rows - 1 or j < 0 or j > cols - 1 or grid[i][j] == 0:
                return 1
            if visited[i][j]:
                return 0
            visited[i][j] = True
            return dfs(i+1, j) + dfs(i-1, j) + dfs(i, j+1) + dfs(i, j-1)
                
        for i in range(rows):
            for j in range(cols):
                if grid[i][j] == 1:
                    return dfs(i, j)
        return -1
```
