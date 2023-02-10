与flex布局区别：
flex布局是轴线布局，只能指定“项目”针对轴线的位置，是一维布局。GRID布局将容器分为行列，可看做二维布局。

+ 单元格：行和列的交叉区域。

### 容器属性

+ `display` 属性

```css
div{
    display:grid;
    //容器元素是块级元素
    display:inline-grid;
    //容器元素是行内块级元素

}
```

**设为grid布局后，容器子元素项目的float/display:inline-block/display:table-cell/verticle-align/column-*等设置都将失效**

+ grid-template-columns/gri-template-rows

repeat()

```css

grid-template-columns:repeat(2,100px,20px,80px);
//repeat参数：重复次数，所要重复的值
grid-template-columns:repeat(auto-fill,100px);
//单元格大小固定但容器大小不固定，希望尽量容纳更多单元格。
```
+ auto-fill关键字进行自动填充

+ fr关键字标识比例关系

//接着看阮一峰














