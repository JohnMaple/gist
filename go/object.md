
### 对象操作

> 打印struct时带上参数名

```go
fmt.Printf("%+v",localRequest)
```


> 打印对象类型

```go
reflect.TypeOf(obj)
```


> 对象复制

```go
func deepCopy(dst, src interface{}) error {
	var buf bytes.Buffer
	if err := gob.NewEncoder(&buf).Encode(src); err != nil {
		return err
	}
	return gob.NewDecoder(bytes.NewBuffer(buf.Bytes())).Decode(dst)
}
```


> 从map中移除

```go
delete(map,"key")
```


> 数组和切片的区分

```
[5]int  数组，值类型

[]int   切片，引用类型
```
 

> 数组定义

```go
adspaces := [2]models.Adspace{}
```

不用new创建的结构体，所有字段都是默认值

> go的range的变量是同一个引用，所以不能在range中传引用，要传值

```go
for _, adspace := range adspaces {
    // adspace始终是同一个引用，如果传&adspace，下一个会被上一个覆盖掉
}
``` 
    
> 对象的作用域

```
package main
import (
	"strconv"
	"fmt"
)

func main() {

	A()

	B()
}

//两个error是同一个对象
func A() {
	_, err := strconv.Atoi("aa")
	fmt.Println(&err)

	b, err := strconv.Atoi("bb")
	fmt.Println(&err)

	fmt.Println(b)
	fmt.Println(err)
}

//两个error不是同一个对象
func B() {
	_, err := strconv.Atoi("ab")

	if err != nil {
		fmt.Println(&err)

		b, err := strconv.Atoi("bb")
		fmt.Println(b)
		fmt.Println(&err)

	}
}
```
