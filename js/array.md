
### 遍历数组的几种方式


> 第一种:普通for循环
```js
for(j = 0; j < arr.length; j++) {
   
}
```
 

> 第二种:优化版for循环

```js
for(j = 0,len=arr.length; j < len; j++) {
   
}
```


> 第三种:弱化版for循环

```js
for(j = 0; arr[j]!=null; j++) {
   
}
```


> 第四种:foreach循环

```js
arr.forEach(function(e){  
   
})
```


> 第五种:foreach变种

```js
Array.prototype.forEach.call(arr,function(el){  
   
});
```


> 第六种:forin循环

```js
for(j in arr) {
   
}
```


> 第七种:map遍历

```js
arr.map(function(n){  
   
});
```


> 第八种:forof遍历(需要ES6支持)

```js
for(let value of arr) {  
   
});
```

