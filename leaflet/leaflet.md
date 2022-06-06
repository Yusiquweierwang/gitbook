# leaflet





### 图标



定义图标类

创建一些有很多共同点的图标。



```javascript
var LeafIcon = L.Icon.extend({
    options: {
        shadowUrl: 'leaf-shadow.png',
        iconSize:     [38, 95],
        shadowSize:   [50, 64],
        iconAnchor:   [22, 94],
        shadowAnchor: [4, 62],
        popupAnchor:  [-3, -76]
    }
});
```

创建实例

```javascript
var greenIcon = new LeafIcon({iconUrl: 'leaf-green.png'}),
    redIcon = new LeafIcon({iconUrl: 'leaf-red.png'}),
    orangeIcon = new LeafIcon({iconUrl: 'leaf-orange.png'});
```





### geojson

geojson对象通过geojson层添加到地图中。

```javascript
L.geoJSON(geojsonFeature).addTo(map);
```



或创建一个空的geojson层，并将其赋给一个变量，以便在以后添加更多特性。

```javascript
var myLayer=L.geoJSON().addTo(map);
myLayer.addData(geojsonFeature);
```



`style`用于以不同方式设置样式。





### 点层pointToLayer





### 过滤（filter）

filter选项可控制geojson功能的可见性。

​	通过一个函数设置filter选项，此函数被geojsoN图层每个元素调用，且通过feature和layer。然后利用该功能属性的值通过返回true false.

```javascript
var someFeatures = [{
    "type": "Feature",
    "properties": {
        "name": "Coors Field",
        "show_on_map": true
    },
    "geometry": {
        "type": "Point",
        "coordinates": [-104.99404, 39.75621]
    }
}, {
    "type": "Feature",
    "properties": {
        "name": "Busch Field",
        "show_on_map": false
    },
    "geometry": {
        "type": "Point",
        "coordinates": [-104.98404, 39.74621]
    }
}];

L.geoJSON(someFeatures, {
    filter: function(feature, layer) {
        return feature.properties.show_on_map;
    }
}).addTo(map);
```































































































