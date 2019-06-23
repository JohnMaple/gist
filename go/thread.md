
### 多线程


> 开启异步线程，匿名方法

```go
go func(){
    fmt.Println("async...")
}()
```

> 使用chain设置超时

```go
ch := make(chan int, 2)
for i := 0; i<2; i++ {
    select {
		case r := <-ch:
			fmt.Println("done ",r)
		case <-time.After(300 * time.Millisecond): //这个时间是最后一次ch有值的超时
			fmt.Println("timeout")
	}
}
```


> 线程休眠

```go
//works
time.Sleep(1000 * time.Millisecond)
    
//fails
var i = 1000
time.Sleep(i * time.Millisecond)
```
    
    

    