[toc]

### 雾

在 cesium 肿 ，雾是大气颜色和地平线上地形的混合。
处于雾中的地形瓦片会增加屏幕空间误差（SSE）。
以此渲染低分辨率的地形。

性能优化比较

http://bingqx.cn/post/Cesium%E4%B9%8B%E9%9B%BE%E7%9A%84%E5%AE%9E%E7%8E%B0

**通过两种特性调节：浓度(density) & 屏幕误差系数(ScreenSpaceError)**

density
[0.0 , 1.0]

screenspaceError
线性增加地形的屏幕误差 ， 因为和相机的距离增加 ， 部分被雾遮挡 。
