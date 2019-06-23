### python2的中文问题

```python

# 大部分情况下，只在文件头（文件的第一行）加上这一行就可以了
# -*- coding=utf-8 -*-
#!/usr/bin/python


# 个别情况下，如果报编码错误，就需要加上下面两行
reload(sys)
sys.setdefaultencoding('utf-8')
```
