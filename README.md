# Vue.js双向绑定的实现原理

Vue.js 最核心的功能有两个，一是响应式的数据绑定系统，二是组件系统。本文仅探究双向绑定是怎样实现的。先讲涉及的知识点，再用简化得不能再简化的代码实现一个简单的 hello world 示例。

 　　参考文章：https://segmentfault.com/a/1190000006599500

一、访问器属性

       访问器属性是对象中的一种特殊属性，它不能直接在对象中设置，而必须通过 defineProperty() 方法单独定义。

       var obj = { };

       // 为obj定义一个名为 hello 的访问器属性

       Object.defineProperty(obj, "hello", {

         get: function () {return sth},

         set: function (val) {/* do sth */}

       })

       obj.hello // 可以像普通属性一样读取访问器属性

       访问器属性的"值"比较特殊，读取或设置访问器属性的值，实际上是调用其内部特性：get和set函数。

       obj.hello // 读取属性，就是调用get函数并返回get函数的返回值

       obj.hello = "abc" // 为属性赋值，就是调用set函数，赋值其实是传参 
       
<p align="center"><img width="100%" src="./images/img (1).png"></p>
