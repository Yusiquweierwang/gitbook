# Prop





<img src="C:\Users\51486\AppData\Roaming\Typora\typora-user-images\image-20220304211735818.png" alt="image-20220304211735818" style="zoom:80%;" />

上图父组件通过`props`向下传递数据给子组件，子组件通过`events`给父组件发送消息。



1.一个良好定义的接口中尽可能将父子组件解耦。







## prop类型

以字符串数组形式列出的prop:

```javascript
props:['title','likes','isPublishes','commentIds','author']
```



若希望每个prop 都有指定的值的类型，则此时可以对象形式列出prop,这些property的名称和值分别是prop各自的名称和类型：

```javascript
props:{
    title:String,
    likes:Number,
    isPublished:Boolean,
    commentIds:Array,
    author:Object,
    callback:Function,
    contactsPromise:Promise
}
```



## 使用prop 传值

1.组件实例的作用域是孤立的，以为着不能在子组件的模板内直接引用父组件的数据。

2.子组件要显式地用prop选项声明它预期的函数：

```html
<div id='box'>
    
    <child message='hell0'></child>
    <child message='234'></child>
</div>

<script>
Vue.component('child',{
    //声明props
    props:['message'],
    //像data一样，prop也可在模板中使用
    //同样也可旨在vm实例中通过this.message来使用
    template:'<span>{{message}}</span>'
})
</script>
```





## 传递静态或动态Prop

+ 静态赋值：

```html
<blog-post title='My journey with Vue'></blog-post>
```

+ 动态赋值：

使用v-bind来动态地将prop绑定到父组件的数据。

每当父组件的数据发生变化时，该变化也会传导给子组件：

```html
<div>
    
   <input v-model='parentMsg'>
   <br>
   <child :my-message='parentMsg'></child>
</div>


```



若想把一个对象的所有属性作为prop传递，可使用不带任何参数的v-bind:

```javascript
var vm=new Vue({
    el:'#box',
    data:{
        todo:{
            text:'learn Vue',
            isComplete:false
        }
    }
})
```

```html
<todo-item :'todo'></todo-item>

<!--等价于-->
<todo-item
           :text='todo.text'
           :is-complete='todo.complete'
           ></todo-item>
```



eg:

```html
<div id='box'>
    <child :'todo'></child>
</div>

<script>
Vue.component('child',{
    props:['text','is-complete'],
    template:'<span>{{text}}</span>',
})
    
    var vm=new Vue({
        el:'#box',
        data:{
            todo:{
                text:'learn vue',
                iscomplete:false
            }
        }
    })
</script>
```

​	





**传入一个数字**

````html
<blog-post v-bind:likes='52'></blog-post>
<!--传入一个数字-->
<blog-post v-bind:likes='post.likes'></blog-post>
<!--用一个变量进行动态赋值-->


````

**传入一个对象**

```html
<blog-post v-bind:author="{
                          name:'veronica',
                          company:'veridian dynamics'
                          }"
           ></blog-post>

<!--用一个变量进行动态赋值-->
<blog-post :author="post.author"></blog-post>
```



### 单向数据流

1.**单向下行绑定**：父级prop的更新会向下流动到子组件中，反过来不行。

2.不能在子组件内部改变prop.



两种常见试图变更prop的情形：

+ **此prop用来传递一个初始值：子组件想将它当作局部数据使用。**此时最好定义一个本地data property并将此prop用作初识值：

```javascript
props:['initialiCounter'],
    data:function(){
        return{
            counter:this.initialCounter
        }
    }
```

+ **此prop作为原始数据传入，由子组件处理成其它数据输出。**

```javascript
props: ['size'],
computed: {
  normalizedSize: function () {
    return this.size.trim().toLowerCase()
  }
}
```



>
>
>在javascript中对象和数组是通过引用传入的，所以对于一个数组或对象类型的prop来说，在子组件中改变此对象或数组本身会影响父组件的状态。



### prop验证



为组件的prop 指定验证要求，若传入数据不合要求，vue会在浏览器控制台强制警告。对于开发给他人使用的组件很有用。



要指定验证规则，需要用对象的形式来定义prop,而不能使用字符串数组：

（之前的字符串数组形式：`props:['todo','doit']`)

对象形式：

```javascript
Vue.component('my-component',{
    props:{
        //基础的类型检查，
        propA:Number,
        //多个可能的类型，
        propB:[String,Number],
        //必填的字符串，
        propC:{
            type:String,
            required:true
        },
        //带有默认值的数字，
        propD:{
            type:Number,
            default:100
        },
        //带有默认值的对象，
        propE:{
            type:Object,
            //对象或数组默认值必须从一个工厂函数获取
            default:function(){
                return {message:'hello'}
            }
        }
    }
})
```





## 非prop 特性

非prop 特性：它可以直接传入组件，而不需要定义相应的prop。









