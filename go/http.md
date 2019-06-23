### HTTP相关


> 简单的文件服务

```go
func main() {
  fs := http.FileServer(http.Dir("/"))
  http.Handle("/",fs)
  http.ListenAndServe("0.0.0.0:30080",nil)
}
```
