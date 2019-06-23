
### 文件操作

> 读取文件

**读取小文件**
```python
for line in open('foo.txt'):
    print line
```

**读取大文件**
```python
with open('foo.txt') as f:
    for line in f:
        print line

# 或

import fileinput
for line in fileinput.input(['foo.log']):
    print line
```