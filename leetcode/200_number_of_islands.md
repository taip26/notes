# 200. Number of Islands

## Strategy:
- use dfs to count the number of islands and mark visited cells to keep track where we've been
- pitfall was where you need to check for visited cells in the termination condition of the recursive function or else you just go back and forth between cells

## Solution:
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        count = 0
        rows, cols = len(grid), len(grid[0])
        visited = [[False for _ in range(cols)] for _ in range(rows)]
        def dfs(i, j):
            if i < 0 or i > rows - 1 or j < 0 or j > cols - 1 or visited[i][j] or grid[i][j] == "0":
                return
            visited[i][j] = True
            dfs(i + 1, j)
            dfs(i - 1, j)
            dfs(i, j + 1)
            dfs(i, j - 1)
        for i in range(rows):
            for j in range(cols):
                if grid[i][j] == "1" and visited[i][j] == False:
                    count += 1
                    dfs(i,j)
        return count
```

