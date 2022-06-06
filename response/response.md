# response

## 响应式是非侵入式的，



数据模型是被代理的javascript对象。当修改时，视图会进行更新。









## vue如何跟踪变化

+ 当一个值被读取时进行跟踪：proxy中的get处理函数中的track函数记录该Property和当前副作用。
+ 当某个值被改变时进行检测：在prxy上调用set处理函数。
+ 重新运行代码读取原始值：trigger函数查找哪些副作用依赖于该property并执行它们。







​	跟踪的是对象 的property 的变化。



**proxy是一个对象，它包装了另一个对象，并允许拦截对该对象的任何交互。**



+ handler-包含捕捉器trap的占位符对象，可译为处理器对象。
+ traps-提供属性方位的方法，类似于操作系统中捕获器
+ target-被proxy代理虚化的对象，作为代理的存储后端

```javascript
const p=new Proxy(target,handler)
```



## reflect



**proxy难点是this绑定**,希望任何方法都绑定到此proxy，而非目标对象，这样就可以拦截它们。解决：es6中引用`reflect`特性。









要为javascript对象创建响应式状态，可使用`reactive`方法：

```javascript
import {reactive} from 'vue'
//响应状态
const state=reactive({
    count:0
})
```

相当于Vue2.x中的Vue.observabable()API,

该api返回一个响应式的对象状态。该响应式转换为“深度转换”--他会影响传递对象的所有嵌套Property.











## ref

ref会返回一个可变的响应式对象，该对象作为一个**响应式的引用**维护着它的内部的值，此即ref名称的来源。

```javascript
import {ref} from 'vue'
const count=ref(0)
console.log(count.value)//0
count.value++
console.log(c)
```



ref是对reactive()的二次包装。

ref定义的数据访问时要多一个.value



### 使用readonly 防止更改响应式对象



## 响应式计算和监听

### computed



```javascript
const count=ref(1)
const plusOne=computed(()=>count.value+1)

console.log(plusOne.value)//2
```



### watchEffect()

为了响应式状态自动应用和重新应用副作用，使用watchEffect()

watchEffect()立即执行传入函数，同时响应式追踪其依赖，并在其依赖变更时重新运行该函数。





```javascript
import {ref,watchEffect} from "vue";

export default{
    setup(){
        const count=ref(0);
        const effect=(()=>console.log(count.value));
        
        setTimeout(()=>count.value++,2000);
        return {count};
    }
}
```

结果打印0和1，0是出于vue响应式设计，在响应式元素（count）依赖收集阶段绘运行以此effect();

1是来自setTimeout里对count加1操作。



### 清除副作用（onInvalidate）

effect中的传递参数，用于清除effect产生的副作用。

只作用于异步函数，并且只在下面两种情况才会被调用：

+ 当effect函数被重新调用时；
+ 当监听器被注销时（如组件被卸载）



```javascript
watchEffect(onInvalidate=>{
    const token=perfomAsyncOperation(id.value)
    onInvalidate(()=>{
        token.cancel()
    })
})
```











# vue更改检测注意事项









## 对对象

对于已创建的实例，vue不允许动态添加根级别的响应式property。但可以使用

`Vue.set(object,propertyName,value)`方法嵌套对象添加响应式property.







# 单文件组件







typescript

