# elementPlus





设计原则

+ 一致
+ 反馈
+ 效率
+ 可控



**全局配置**

在引入elementUI时，传入一个包含size  zIndex属性的全局对象。size表示表单组件的默认尺寸，zIndex用于设置弹出组件的层级



```javascript
import {createApp} from 'vue'
import ElementPlus from 'element-plus'
import App from './App.vue'

const app=createApp(App)
app.use(ElementPlus,{size:'small',zIndex:3000})
```









### custom theme

$colors:()!default; 作为map来保存不同类型的颜色。

$notification 是所有notification 组件的变量的映射。







### 内置过度动画



+ Fade淡入淡出
+ zoom缩放
+ collapse折叠面板
+ 





### scrollbar

滚动条



















