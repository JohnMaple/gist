---
title: Front
date: 2017-07-02 18:48:12
tags:
---


# UI

viewport 视觉窗口
    
breadcrumb 面包屑
    
减少多个js操作同一块html
减少一个页面上的各种id

disable和readonly的区别：http://www.cnblogs.com/sgivee/archive/2010/06/02/1750201.html
disable的表单不会提交，需要使用readonly

    
display和hidden，尽量使用display

    display:none ---不为被隐藏的对象保留其物理空间，即该对象在页面上彻底消失 
    visible:hidden--- 使对象在网页上不可见，但该对象在网页上所占的空间没有改变

jquery扩展方法，http://www.jb51.net/article/28440.htm
    
    1. jQuery.extend(Object);　　　// jQuery 本身的扩展方法 
    2. jQuery.fn.extent(Object);　 // jQuery 所选对象扩展方法 
    
使用事件监听实现样式和js的分离


CSS文字超出长度的显示省略号

语法：` text-overflow ： clip | ellipsis `

取值：
`
    clip：
    不显示省略标记（...），而是简单的裁切。
    ellipsis：
    当对象内文本溢出时显示省略标记（...）
`
说明：
`
    设置或检索是否使用一个省略标记（...）标示对象内文本的溢出。对应的脚本特性为textOverflow。
    text-overflow属性仅是注解，当文本溢出时是否显示省略标记。并不具备其它的样式属性定义。要实现溢出时产生省略号的效果还须定义：强制文本在一行内显示（white-space:nowrap）及溢出内容为隐藏（overflow:hidden），只有这样才能实现溢出文本显示省略号的效果。
`
例子：` { overflow: hidden; text-overflow: ellipsis;   white-space: nowrap;    otextoverflow: ellipsis;width: 30px; } `
`
    说明： 以下3 个属性要一起设置，并且要给容器设置宽度，如果是表格的话要将布局方式改为table-layout:fixed。
     verflow: hidden;
     text-overflow:ellipsis;
     white-space:nowrap;  
`


ajax请求示例
```javascript

$.ajax({    
    url:"${pageContext.request.contextPath}/public/testupload",
    type:"post",
     data: JSON.stringify({
        userId: userId,
        name: name,
        sex: sex,
        age: age,
        mobile: mobile,
        email: email,
        type: type
     }),
    success:function(data){
        window.clearInterval(timer);
        console.log("over..");
    },
    error:function(e){
        alert("错误！！");
        window.clearInterval(timer);
    }
});


// 扩展jquery的序列化
(function ($) {
  $.fn.serializeJson = function () {
    var serializeObj = {}
    var array = this.serializeArray()
    var str = this.serialize()
    $(array).each(function () {
      if (serializeObj[this.name]) {
        if ($.isArray(serializeObj[this.name])) {
          serializeObj[this.name].push(this.value)
        } else {
          serializeObj[this.name] = [serializeObj[this.name], this.value]
        }
      } else {
        serializeObj[this.name] = this.value
      }
    })
    return serializeObj
  }
})
  
```
