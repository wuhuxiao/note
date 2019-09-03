# 模拟点运动图层

## 原理

通过对graphiclayer的不断刷新，加载变换的数据源，注意深、浅拷贝，使用clone\(\)方法

```text
graphics = graphiclayer.graphics.clone();
//获取数据源，使用深拷贝，不改变原数据源
timer = setInterval(() => {
            //临时运动图层初始化，清空
            movelayer.removeAll();
            linemovelayer.removeAll();
            for (var i = 0; i < selectedGraphics.length; i++) {
            //根据数据源的属性信息如，车辆的方向
              var angle =
                ((2 * Math.PI) / 360) * graphics[i].attributes.direction;
              //循环运动，运动50次后，回到起点
              if (movecounts == 50) {
                graphics[i].geometry.x -= 0.025 * Math.sin(angle);
                graphics[i].geometry.y -= 0.025 * Math.cos(angle);
                graphics[i].geometry.paths[0] = graphics[i].geometry.paths[0].slice(0, 1)
              } else {
                graphics[i].geometry.x += 0.0005 * Math.sin(angle);
                graphics[i].geometry.y += 0.0005 * Math.cos(angle);
                graphics[i].geometry.paths[0].push([selectedGraphics[i].geometry.x, selectedGraphics[i].geometry.y
                ])
              }
              var graphic = selectedGraphics[i].clone();
              graphic.symbol.angle = graphic.attributes.direction - 90;
              movelayer.add(graphic);

              var lineGraphic = selectedLineGraphic[i].clone();
              linemovelayer.add(lineGraphic);
              if (movecounts == 50) {
              movecounts = 0;
            }
            },150)

```



