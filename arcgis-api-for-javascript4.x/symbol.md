# 2DSymbol



| 类型 | 渲染 |
| :--- | :--- |
| 点 |  [SimpleMarkerSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-SimpleMarkerSymbol.html), [PictureMarkerSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-PictureMarkerSymbol.html), [TextSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-TextSymbol.html) |
| 线 |  [SimpleLineSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-SimpleLineSymbol.html), [TextSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-TextSymbol.html) |
| 面 |  [SimpleFillSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-SimpleFillSymbol.html), [PictureFillSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-PictureFillSymbol.html), [SimpleMarkerSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-SimpleMarkerSymbol.html), [TextSymbol](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-TextSymbol.html) |

## SimpleMarkerSymbol

```javascript
var symbol = {
  type: "simple-marker",  // autocasts as new SimpleMarkerSymbol()
  style: "square",//circle,cross,diamond,square,triangle,x
  color: "blue",
  size: "8px",  // pixels
  outline: {  // autocasts as new SimpleLineSymbol()
    color: [ 255, 255, 0 ],
    width: 3  // points
  },
  xoffset: 2px,
  yoffset: 2px
};
```

## PictureMarkerSymbol

```javascript
var symbol = {
  type: "picture-marker",  // autocasts as new PictureMarkerSymbol()
  url: "https://static.arcgis.com/images/Symbols/Shapes/BlackStarLargeB.png",
  width: "64px",
  height: "64px",
  angle: 45,
  xoffset: 2px,
  yoffset: 2px
};
```

## TextSymbol

```javascript
var textSymbol = {
  type: "text",  // autocasts as new TextSymbol()
  color: "white",
  //光晕
  haloColor: "black",
  haloSize: "1px",
  text: "You are here",
  xoffset: 3,
  yoffset: 3,
  font: {  // autocasts as new Font()
    size: 12,
    family: "Josefin Slab",
    weight: "bold"
  },
  angle: 45,
  backgroundColor: "black",
  borderLineColor: "black",
  borderLineSize: 2,
  horizontalAlignment :"",//left | right | center | justify
  kerning : true,//是否适应字距
  rotated : false//是否旋转
  verticalAlignment :"",// baseline | top | middle | bottom
  
};
```

## SimpleLineSymbol



## SimpleFillSymbol

## PictureFillSymbol



