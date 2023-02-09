# ES6























## 内置对象和原生对象

Build-in 

Native

区别：

前者总是在引擎初始化阶段就创建好的对象，是后者的一个子集；

后者包括了一些在运行过程中 **动态创建** 的对象。

![图片描述](https://segmentfault.com/img/bVlc8F)











原生对象：独立于宿主环境的ecmascript实现提供的对象。

```javascript
Object;
Function;
Array;
String;
Boolean;
Number;
Date;
RegExp;
Error;
EvalError;
RangeError;
...
```



内置对象：不需要New,独立于宿主环境，在一个脚本程序运行的开始处。



### function*

此声明方式会定义一个生成器函数（generator function），返回一个generator对象。









### yield 



用来暂停和恢复一个生成器函数（function 或 遗留的生成器函数）

```javascript
function* countAppleSales(){
    var saleList=[3,6,4];
    for(var i=0;i<saleList.length;i++){
        yield saleList[i];
    }
}
var appleStore=countAppleSales(); //
console.log(appleStore.next());//{value:3,done:false}
console.log(appleStore.next());//{value:7,done:false}
console.log(appleStore.next());//{value:4,done:tr}
```















