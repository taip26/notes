# 155. Min Stack

strats:
  - you only have to keep track of the min value changes when you push/pop... so keep track with another stack!!!!!!!


```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.min = []

    def push(self, val: int) -> None:
        idx = len(self.stack)
        if len(self.stack) == 0:
            self.min.append(0)
        else:
            if val < self.stack[self.min[-1]]:
                self.min.append(idx)
            else:
                self.min.append(self.min[-1])
        self.stack.append(val)
        

    def pop(self) -> None:
        self.stack.pop(-1)
        self.min.pop(-1)
        

    def top(self) -> int:
        return self.stack[-1]
        

    def getMin(self) -> int:
        return self.stack[self.min[-1]]
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
