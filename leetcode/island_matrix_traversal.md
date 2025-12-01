# 2. Island Matrix Traversal

Notes gathered from this source: https://www.linkedin.com/pulse/islands-matrix-traversal-design-pattern-manas-rath-shifc/

General strategy - Traverse the matrix, when encountering an "island" use BFS/DFS to find connected components and mark all visited cells. Every time a BFS/DFS is initiated, increment counter

Associated LeetCodes:
 - 200. Number of Islands
   - http://leetcode.com/problems/number-of-islands/description/

```python
def bfs(node):
    nodes = deque()
    nodes.append(neighbor for neighbor in curr.neighbors)
    while !nodes.empty:
        visitNode = nodes.pop()
        nodes.append(neighbor for neighbor in visitNode.neighbors)
visited = [[False for cell in grid[0]] for row in grid] # Initialize visiting map
count = 0
for r in range(len(grid)):
    for c in range(len(grid[0])):
        if grid[r][c] == "1" and visited[r][c] == False:
            count += 1
            nodes = deque().append((r, c)) # Add current node to search
            while !nodes.empty():
                i, j = nodes.pop()
                visited[i][j] = True
                # Add neighbors
                if i-1 >= 0 and visited[i-1][j] == False:
                    nodes.append((i-1,j))
                if j-1 >= 0 and visited[i][j-1] == False:
                    nodes.append((i,j-1))
                if i+1 < len(grid) and visited[i+1][j] == False:
                    nodes.append((i+1,j))
                if j-1 < len(grid[0]) and visited[i][j+1] == False:
                    nodes.append((i,j+1))
return count

```
