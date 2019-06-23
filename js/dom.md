> 获取、修改img标签的src属性

实例：`<img id="imgId" src="/images/demo.jpg" tSrc="/images/demo1.jpg" alt="" />`

方法一
```js
var obj = document.getElementById("imgId");
var imgSrc = obj.getAttribute("src");
var realSrc = obj.getAttribute("tSrc");

// 修改src属性
var imgSrc = obj.setAttribute("src", "new_src");
var realSrc = obj.setAttribute("tSrc", "new_tSrc");
```

方法二

```js
var obj = document.getElementById("imgid");
var imgSrc = obj.src;
var realSrc = obj.tSrc;//提示undefined，即tSrc属性没有定义，不能获取到

obj.src = imgSrc; // 正常
obj.tSrc = realSrc; // 提示undefined，即tSrc属性没有定义，设置失败
```


> 获取父级、子级、兄弟节点

原生javascript方法：
```js
var a = document.getElementById("dom");

var b = a.childNodes; //获取a的全部子节点；

var c = a.parentNode; //获取a的父节点；w3c标准
var c = a.parentElement

var d = a.nextSibling; //获取a的下一个兄弟节点
var e = a.previousSibling; //获取a的上一个兄弟节点
var f = a.firstChild; //获取a的第一个子节点
var g = a.lastChild; //获取a的最后一个子节点
```

jQuery方法：
```js
jQuery.parent(expr) //找父亲节点，可以传入expr进行过滤，比如$("span").parent()或者$("span").parent(".class")

jQuery.parents(expr) //类似于jQuery.parents(expr),但是是查找所有祖先元素，不限于父元素

jQuery.children(expr) //返回所有子节点，这个方法只会返回直接的孩子节点，不会返回所有的子孙节点

jQuery.contents() //返回下面的所有内容，包括节点和文本。这个方法和children()的区别就在于，包括空白文本，也会被作为一个jQuery对象返回，children()则只会返回节点

jQuery.prev() //返回上一个兄弟节点，不是所有的兄弟节点

jQuery.prevAll() //返回所有之前的兄弟节点

jQuery.next() //返回下一个兄弟节点，不是所有的兄弟节点

jQuery.nextAll() //返回所有之后的兄弟节点

jQuery.siblings() //返回兄弟姐妹节点，不分前后

jQuery.find(expr)  //跟jQuery.filter(expr)完全不一样。jQuery.filter()是从初始的jQuery对象集合中筛选出一部分，而jQuery.find()的返回结果，不会有初始集合中的内容，比如$("p"),find("span"),是从p元素开始找,等同于$("p span").
```