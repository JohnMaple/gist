
### 字符串操作

> 去除字符串两边的空格

```python
s = ' abc '
print s.strip()
```


> 去除字符串两边的换行符

```python
print "abc".strip('\n')
```

> 字符串格式化

1、需要指定类型
```python
print("I'm %s. I'm %d year old" % ('Vamei', 99))
```
2、format函数，不需要指定类型，更灵活
```python
# 不设置指定位置，按默认顺序
"{} {}".format("hello", "world")    
'hello world'
 
# 设置指定位置
"{0} {1}".format("hello", "world")  
'hello world'
 
# 设置指定位置
"{1} {0} {1}".format("hello", "world") 
'world hello world'
print("网站名：{name}, 地址 {url}".format(name="教程", url="www.hostname.com"))

# 通过字典设置参数
site = {"name": "教程", "url": "www.hostname.com"}
print("网站名：{name}, 地址 {url}".format(**site))

my_list = ['教程', 'www.hostname.com']
print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))  # "0" 是必须的
```