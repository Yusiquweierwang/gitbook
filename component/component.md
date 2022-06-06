# component





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





















## 组件注册









**全局注册**

注册之后可用在任何新创建的vue根实例(new Vue)的模板中





```javascript
Vue.component('my-component-name',/*...*/)

```

需要在初始化实例之前注册组件,即：

```javascript
Vue.component('my-component-name',{
    //...
}),//注册组件

var vm=new Vue({
    el:"#some-element",
})//创建根实例
```



选项中添加`template`，就是对html的构造:

```html
<div id='example'>
    <div>a custom component</div>
</div>

<script>
Vue.component('component',{
    template:'<div>a custom component'</div>'
})

//创建根实例
new Vue({
    el:'#example'
})
</script>
```







**局部注册**

通过普通的javascript对象来定义组件，通过某个Vue实例/组件的实例选项`component`注册仅在其作用域可用的组件,如下例只在box1显示而在box2不显示：

```html
<div id='box'>
    <my-component></my-component>
</div>

<div id='box2'>
    <my-component></my-component>
</div>
<script>
var Child={
    template:'<div>a cat</div>'
}

var vm=new Vue({
    el:'#box',
    components:{
        'my-component':Child
    }
})

var vm=new Vue({
    el:'#box2'
})
</script>
```



```javascript
var ComponentA={//...
}
var ComponentB={
    //...
}
var ComponentC={
    //...
}
```

在`component`选项中定义想要使用的组件：

```javascript
new Vue({
    el:'#app',
    components:{
        'component-a':ComponentA,
        'component-b':ComponentB
    }
})
```

对于component对象中的每个property来说，其property名即自定义元素的名字，property值即此组件的选项对象。



**局部注册的组件在其子组件中不可用**

在`ComponentB`中使用`ComponentA`:

[1]

```javascript
var ComponentA={
    //...
}

var ComponentB={
    components:{
        'component-a':ComponentA
    }
}
```



[2]通过Babel和webpack使用ES2015模板：

```javascript
import ComponentA from './ComponentA.vue'

export default{
    components:{
        ComponentA
    }
}
```

在 ES2015+ 中，在对象中放一个类似 `ComponentA` 的变量名其实是 `ComponentA: ComponentA` 的缩写，即这个变量名同时是：

- 用在模板中的自定义元素的名称
- 包含了这个组件选项的变量名





## data必须是函数







```javascript
Vue.component('mine',{
    template:'<span>{{message}}</span>',
    data:{
        message:'hello'
    }
})
```

上式vue会停止运行，控制台发挥出警告。





















## 模块系统







```javascript
import ComponentA from './ComponentA'
import ComponentC from './ComponentC'

export default {
    components:{
        ComponentA,
        ComponentC
    },
    //...
}
```

此时可在ComponentB模板中使用ComponentC和ComponentA.



## 基础组件自动化全局注册



若组件只是包裹了一个输入框或按钮之类相对通用的元素，称之为基本组件。

会导致很多组件里会有包含基础组件的长列表：

```javascript
import BaseButton from './BaseButton.vue'
import BaseIcon from './BaseIcon.vue'
import BaseInput from './BaseInput.vue'

export default {
    components:{
        BaseButton,
        BaseIcon,
        BaseInput
    }
}
```



```javascript

```



















