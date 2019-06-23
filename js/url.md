
### URL操作

> window.location.href (设置或获取整个 URL 为字符串)

```js
var test = window.location.href;
alert(test);
//  返回：http://i.cnblogs.com/EditPosts.aspx?opt=1
```


> window.location.protocol (设置或获取 URL 的协议部分)

```js
var test = window.location.protocol;
alert(test);
//返回：http:
```


> window.location.host (设置或获取 URL 的主机部分)

```js
var test = window.location.host;
alert(test);
//返回：i.cnblogs.com
```


> window.location.port (设置或获取与 URL 关联的端口号码)

```js
var test = window.location.port;
alert(test);
//返回：空字符(如果采用默认的80端口 (update:即使添加了:80)，那么返回值并不是默认的80而是空字符)
```


> window.location.pathname (设置或获取与 URL 的路径部分（就是文件地址）)

```js
var test = window.location.pathname;
alert(test);
//返回：/EditPosts.aspx
```


> window.location.search (设置或获取 href 属性中跟在问号后面的部分)

```js
var test = window.location.search;
alert(test);
//返回：?opt=1
```
（PS：获得查询（参数）部分，除了给动态语言赋值以外，我们同样可以给静态页面，并使用javascript来获得相信应的参数值。）


> window.location.hash (设置或获取 href 属性中在井号“#”后面的分段)

```js
var test = window.location.hash;
alert(test);
//返回：空字符(因为url中没有)
```
