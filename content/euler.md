Title: Solution for ProjectEuler
Date: 2016-10-11
Category: ProjectEuler
Description:
http://projecteuler.net/

Task
====

+ Push code to github.
+ Each module solves 1 problem.
+ In this form below.


_base.py_
```python
#!/usr/bin/env python3


class Problem(object):
    def __init__(self, number):
        self.number = number

    def solve(self):
        return 'No solution given yet!'
```

example : _pe1.py_
```python
#!/usr/bin/env python3
from base import Problem


class Solution(Problem):
    def solve(self, input_):
        print('Solving problem {}'.format(self.number))
        print('Result: {}'.format(sum([i for i in range(input_) if i % 3 == 0 or i % 5 == 0])))


if __name__ == '__main__':
    solution = Solution(1)
    solution.solve(1000)
```
