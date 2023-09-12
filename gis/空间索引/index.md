[toc]

## 空间数据查询类型

### 最邻近查询

K-MEANS 最邻近算法

### 范围查询

### R-tree & K-D tree

![Alt text](http://static.zybuluo.com/bingqixuan/xyf2squeaa24zhzcddnwle81/11.png)
对于 100 万个点 ， 在 r-tree 中每个节点有 9 个子节点的示例中， 树的高度：

```matlab
ceil(log(1000000))/log(9)) = 7
```

r- tree 范围搜索平均花费 O(K\*log(n))

（较高的值意味着更快的索引和更慢的查询 ，反之亦然）

### KNN K 最邻近查询
