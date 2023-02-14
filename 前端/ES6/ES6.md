[toc]
# ES6






## Babel转码器

+ Babel转码器

可以将ES6代码转为ES5代码。





##  let var const
**const本质不是保证变量值不改动，而是变量指向的内存地址所保存的数据不能改动。**
**即对简单类型数据：数值/字符串/布尔值等同于常量，对复合类型数据：对象/数组只保证指针固定。**
```javascript
const foo={};
//为foo添加一个属性，可以成功
foo.prop=13;
foo.prop;//13
```
将对象冻结：**Object.freeze()**



## 解构赋值（Destructing）


## 模板字符串



## 内置对象和原生对象

Build-in 

Native

区别：

前者总是在引擎初始化阶段就创建好的对象，是后者的一个子集；

后者包括了一些在运行过程中 **动态创建** 的对象。

![图片描述](https://segmentfault.com/img/bVlc8F)


## RegExp构造函数



## 数值扩展
### 扩展运算符(...)
可以在函数调用/数组构造时，将数组表达式或者string在语法层面展开，；还可在构造对象时，将对象表达式按key-value方式展开。

Number.parseInt()

Number.isInterger()

**Math对象的扩展**

## 函数的扩展
### 函数参数的默认值
（看看这个https://www.bookstack.cn/read/es6-3rd/spilt.2.docs-function.md）

### rest(...变量名)
用于获取函数的多余参数，这样就不需要`arguments`对象了。
利用rest参数可以向函数传入任意数目的参数。
```javascript
//argumenet变量的写法
function sortNumbers(){
    return Array.prototype.slice.call(arguments).sort(); iiij;
}

//rest写法
const sortNumbers=(...numbers)=>numbers.sort();
```

## 原生对象：独立于宿主环境的ecmascript实现提供的对象。

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


## 类
+ 创建：
 ```javascript
  class Star{
    ...
  }
```
+ 利用类创建对象：
```
  var star=new Star();
  ```
### constructor()
是类的构造函数方法（默认方法），用于1.传递参数，2.返回实例对象。
**（会自动创建）**
```javascript
class Star{
    constructor(uname){
        this.uname=uname;
    }
    //类里函数不需要写fun,后面不需要写“，”
    sing(){
        console.log("sing");
    }
}
//利用类创建对象
var ldh=new Star('刘德华');
var zxy=new Star('张学友');
```
### 类的继承
```javascript
class Father{
    constructor(){
        //...
    }
    money(){
        console.log(3000);
    }
}
class Son extends Father{

}
var son=new Son();
son.money();//3000 
```
+ **super关键字**
  用于访问对象字面量或类的原型（[[prototype]])上的属性，或调用父类中的构造函数。 
```javascript
class Father {
    constructor(x,y){
        this.x=x;
        this.y=y;
    }
    sum(){
        console.log(this.x+this.y)
    }
}
class Son extends Father{
    constructor(x,y){
        super(x,y);
        //调用父类中的构造函数
    }
}
var son=new Son(1,2);
son.sum();//3
```
也可以调用父类中的普通函数
```javascript
class Father {
    say(){
        return ''
    }
}
```
```javascript
class Person{
    constructor(surname){
        this.surname=surname;
    }
}
class Student extends Person{
    constructor(surname,firstname){
        super(surname);//调用父类constructor;
        this.firstname=firstname;//定义子类独有属性
    }
}
```
**1.子类在构造函数中使用super,必须放在this前面（必须先调用父类构造方法，再使用子类构造方法；
2.类里面共有属性和方法一定要加this使用；
3.constructor里面的this指向的是实例对象**



















