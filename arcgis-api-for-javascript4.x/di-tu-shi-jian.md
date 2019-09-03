# 地图事件之地图状态监听

## watch

```javascript
	mainView.watch("extent", updateOverviewExtent);	
```

watch方法是accessor类的方法，只要是继承它的都可以监听具体的属性。Arcgis api 的所有类都继承accessor类，因此此方法最通用

## watchUtils.when

```javascript
    watchUtils.when(mainView, "stationary", updateOverview);
```

watchUtils.when方法也是监听，但是只有监听的属性为true 时，才执行给定的方法

## view.whenLayerView

监听图层加载完成，当图层加载完成后，调用之后的方法

```javascript
view.whenLayerView(featureLayer).then(function(layerView) {
          layerView.watch("updating", function(value) {
          }
}
```



