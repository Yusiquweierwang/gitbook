# mvvm和mvc





MVC要实现的目标是将软件用户界面和页面逻辑分离以使代码扩展性，可复用性，可维护性，灵活性增强。



少用继承，多用组合

is-a    has-a



### 继承问题：继承层次过深，关系过于复杂会影响到代码的可读性和可维护性。



### 组合 composition 接口 委托delegation 



组合即A类对象是B类的成员变量（整体和部分关系）

```java
class 电池{
    public void 放电(){
        System.out.println('output');
    }
}
class 屏幕{
    public void 亮屏(){
        System.out.println('显示内容');
    }
}
class 手机{
    private 电池 dc;
    private 屏幕 pm;
    
}
public 开机(){
    dc.放电();
    pm.亮屏();
}
```



### 区别

+ **继承**结构中，父类的内部细节对子类可见，可通过继承的代码复用是一种白盒式代码复用，

+ 若父类的实现跟随版本而发生改变，则子类的实现也将随之改变。



+ **组合**通过现有类拼装。在现有类间，各内部细节不可见，因此此方式代码复用是黑盒式代码复用









## MVC

组成MVC的三个模式：组合模式，策略模式，观察者模式。



view:用户界面，传送指令到controller

controller：业务逻辑，完成业务逻辑后，要求model改变状态。

model：数据保存，将新的数据发送到view，用户得到反馈。



降低了项目耦合。但并未限制数据流，model 和 view 之间可以通信。



## MVVM

采用双向数据绑定：view的绑定，自动反映在viewmodel上。





