
### 日期操作


> 日期格式化

```go
fmt.Println(t.Format("2006-01-02 15:04:05 -0700"))
fmt.Println(t.Format("2006-01-02 15:04:05"))
```

> 时间变量传值时，需要把int类型转成duration类型

```go
time.Duration(100) * time.Millisecond
```