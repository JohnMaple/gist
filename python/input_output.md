

> 禁用python输出时的缓存  

```bash
> nohup Python test.py > nohup.out 2>&1 &
```

发现nohup.out中显示不出来python程序中print的东西。这是因为python的输出有缓冲，导致nohup.out并不能够马上看到输出。
python 有个-u参数，使得python不启用缓冲。
```bash
> nohup python -u test.py > nohup.out 2>&1 &
```


> print

```python
# 换行输出
print 'abc'

# 不换行输出，print语句中使用逗号来抑制自动生成的换行符号
# 如果我们不抑制print语句产生的换行符号，每行在显示时就会有额外的空行产生。
print 'abc', 
```  
