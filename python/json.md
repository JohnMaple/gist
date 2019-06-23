
### Json操作

> 对象转Json字符串

```python
import json

dict = {}
dict['entity'] = 'visit_id'
print json.dumps(dict, encoding="UTF-8", ensure_ascii=False)
```


> 字符串转成json

````python
user_str = "{'name' : 'jim', 'sex' : 'male', 'age': 18}"

# eval() 函数
user_obj = eval(user_str)

# json.loads() 函数
user_obj = json.loads(user_str)
````