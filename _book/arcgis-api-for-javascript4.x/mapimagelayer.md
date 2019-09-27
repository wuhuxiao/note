# MapImageLayer

## 使用场景

调用Arcgis Server上面的地图服务时

当地图服务中有多个图层时，使用sublayers进行图层管理

```text
var layer = new MapImageLayer({
          url:
            "https://sampleserver6.arcgisonline.com/arcgis/rest/services/Census/MapServer",
          title: "Census Demographics",//图层标签，方便筛选
          sublayers: [
            {
              id: 0,//对应server上的图层编号，必要属性
              title: "Population/square mile",
              renderer: populationRenderer,//自定义图层渲染，覆盖server上面初始的渲染
              visible: false,//可以控制图层显示与否
              //自定义标签
              labelingInfo: [
                {
                  labelExpression: "[POP2007]",
                  labelPlacement: "always-horizontal",
                  symbol: {
                    type: "text", // autocasts as new TextSymbol()
                    color: "white",
                    haloColor: "#3d6a89",
                    haloSize: 1,
                    font: {
                      size: 10
                    }
                  },
                  minScale: 37000
                }
              ],
              //图层内要素的弹出模板
              popupTemplate: {
                // autocasts as new PopupTemplate()
                title: "{states.STATE_NAME}",
                content: [
                  {
                    type: "fields",
                    fieldInfos: [
                      {
                        fieldName: "states.POP2007",
                        label: "Total population",
                        visible: true,
                        format: {
                          digitSeparator: true,
                          places: 0
                        }
                      },
                    }
                    ]
                  }
                ]
              },
              opacity: 0.6,//图层透明度0~1,0表示不透明
              source: {
                mapLayerId: 1//数据源 对应server上的图层编号，必要属性
              }
            }
          ]
        });

```

筛选出图层

```text
var norwegianSublayer = layer.sublayers.find(function(sublayer) {
          return (
            sublayer.title === "Share of population with Norwegian Ancestry"
          );
        });
```

对指定图层进行查询

```text
                    var querylayer = mapserverlayer.findSublayerById(
                      parseInt(index)//需要查询操作的图层id
                    );
                    var query = querylayer.createQuery();
                    query.geometry = point;//空间查询
                    query.outFields = ["*"];
                    query.distance = 2;
                    query.units = "miles";
                    query.returnGeometry = true;
                    querylayer.queryFeatures(query).then(function(result) {
                      if (result.features.length > 0) {
                        view.popup.open({
                          location: point,
                          features: result.features
                        });
                        return;
                      }
                    });
```



