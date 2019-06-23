
### Json操作

> 对象转成json

```go
json.Marshal(ad_obj)
```


> 如果value为空不显示key

```go
struct article {
   descrtiption string `json:"descrtiption,omitempty"`
} 
```
    