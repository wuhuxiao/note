# 地图事件之点击

```javascript
view.on("click", function(event) {
    //可以直接调用event的地图坐标进行空间查询
    //也可以使用封装的方法进行点击查询
    
    view.hitTest(screenpoint).then(function(response) {
    //screenpoint是屏幕坐标
    //查询对象是featurelayer和graphiclayer，mapserver里面的图层不参与查询，
    //若想让其中的图层参与查询，参考mapimagelayer中的用法
    })
})
```

