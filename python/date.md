### 日期相关操作

>  获取昨天的日期

```python
from datetime import timedelta, datetime

yesterday = datetime.today() + timedelta(-1)

```


> 日期格式化

```python
from datetime import datetime

day = datetime.today().strftime('%Y_%m_%d')
print day
```
