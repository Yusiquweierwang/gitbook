[toc]

cesium supported format：

- 影像数据：
  Bing 天地图 arcgis OSM WMTS WMS
- 地形数据：
  ArcGIS Google STK
- 矢量数据：
  KML KMZ GeoJSON TopoJSON CZML
- 三维模型：
  GLTF GLB
- 三维瓦片：
  3D Tiles（倾斜摄影、人工模型、三维建筑物、CAD、BIM、点云数据）等

### cesium knowledge system：

- web 前端
- Graphics:
  vertex normal texture material shader
- GIS:
  vector raster wkt epsg wms wfs geojson kml

### cesium learning route

- **Viewer Class**
  一切 API 的入口

- **Camera Class**
  Cartesian3 & Cartographic

- **ImageryLayer Class**
  ImageryProvider Class

- **TerrainProvider**
  SampleTerrain

- **Entity API**
  DataSource & Scene.pick & Property

- **Cesium3DTiles**
  Cesium3DTiles Class

- **Primitive API**
  GeometryInstance Class & Geometry Class

- **Fabric**
  Appearance Class & Material

- **ParticleSystem**
  Particle Class ParticleF

### 初始界面

![Alt text](https://pic1.zhimg.com/80/v2-fa9874b38ed404083b71e2d376925aac_720w.webp?source%3Dd16d100b)

```javascript
var viewer = new Cesium.Viewer("cesiumContainer", {
  animation: false, //动画小组件
  baseLayerPicker: false, //底图组件，选择三维数字地球的底图（imagery and terrain)
  fullScreenButton: false, //全屏组件
  vrButton: false, //vr 模式
  geoCoder: false, //地理编码（搜索组件）
  homeButton: false, //首页，点击后跳转到默认视角
  infoBox: false, //信息框
  sceneModelPicker: false, //场景模式：切换2d ， 3d 和 columbus view (CV) 模式
  selectionIndicator: false, //是否显示选取指示器组件
  timeline: false, //时间轴
  navigationHelpButton: false, //帮助提示 ，如何操作数字地球
  navigationInstructionsInitiallyVisible: false,
});

//隐藏logo
viewer._cesiumWidget._creditContainer.style.display = "none";
```
