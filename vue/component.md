# 组件





```javascript
// 定义一个名为 button-counter 的新组件
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})
```



组件是可复用的vue实例



可通过`new Vue`创建的vue根实例中，把此组件作为自定义元素使用。

```html
<div id="component-demo">
    <button-counter></button-counter>
</div>

<script>
 new Vue({
     el:'#component-demo'
 })
</script>
```





**data必须是一个函数**

定义<button-counter>组件时，data并不像下面一样直接提供一个对象：

```javasacript
data:{
	count:0
}
```

**而是一个组件的data选项必须是一个函数**，因此每个实例可维护一份被返回对象的独立的拷贝：

```javascript
data:function(){
    return{
        count:0
    }
}
```



如果vue无此规则，则点击一个按钮可能会像如下代码一样影响到其他所有实例：

![image-20220304165220201](C:\Users\51486\AppData\Roaming\Typora\typora-user-images\image-20220304165220201.png)





## 组件的组织



嵌套的组件树：

![image-20220304165258720](C:\Users\51486\AppData\Roaming\Typora\typora-user-images\image-20220304165258720.png)





### 通过`Prop`向子组件传递数据



prop是可以在组件上注册的一些自定义attribute.

作用是父组件向子组件单向传递数据









## Vue组件通信方式





父子组件：

>
>
>prop
>
>$emit
>
>[$root,
>
>$parent,
>
>$children]













## provide/inject 处理响应性

```javascript
const app = Vue.createApp({})

app.component('todo-list', {
  data() {
    return {
      todos: ['Feed a cat', 'Buy tickets']
    }
  },
  provide: {
    user: 'John Doe'
  },
  template: `
    <div>
      {{ todos.length }}
      <!-- 模板的其余部分 -->
    </div>
  `
})

app.component('todo-list-statistics', {
  inject: ['user'],
  created() {
    console.log(`Injected property: ${this.user}`) // > 注入的 property: John Doe
  }
})
```





## 异步组件

应用中，需要将应用分隔成小一些的代码块，只在需要的时候才从服务器加载一个模块。





























































