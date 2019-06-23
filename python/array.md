### 数组操作

> 字符串数组转换成整型数组

python2.x
```python
arr = ['22','44','66','88']
arr = map(int,arr)
print(arr)
```

python 3.x
```python
arr = ['22','44','66','88']
arr = list(map(int,arr))
print(arr)
```