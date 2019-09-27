# Renderer

| 需求 | 实现需求的渲染 |
| :--- | :--- |
| 只根据位置信息渲染 | SimpleRenderer,  HeatmapRenderer |
| 根据属性唯一值渲染 | UniqueValueRenderer |
| 分段值渲染 | ClassBreakRenderer |
| 连续值，多字段渲染 | SimpleRenderer，UniqueValueRenderer，visualVariables |

## SimpleRenderer

```text
renderer = {
  type: "simple",  // autocasts as new SimpleRenderer()
  symbol: { type: "simple-fill" },  // autocasts as new SimpleFillSymbol()
  visualVariables: [{
    type: "color",
    field: "POPULATION",
    normalizationField: "SQ_KM",
    // features with 30 ppl/sq km or below are assigned the first color
    stops: [{ value: 100, color: "#FFFCD4" },
          { value: 500, color: "#0D2644" }]
  }]
};
```

## HeatmapRenderer

```text
renderer = {
  type: "heatmap",
  field: "crime_count",
  colorStops: [
    { ratio: 0, color: "rgba(255, 255, 255, 0)" },
    { ratio: 0.2, color: "rgba(255, 255, 255, 1)" },
    { ratio: 0.5, color: "rgba(255, 140, 0, 1)" },
    { ratio: 0.8, color: "rgba(255, 140, 0, 1)" },
    { ratio: 1, color: "rgba(255, 0, 0, 1)" }
  ],
  minPixelIntensity: 0,
  maxPixelIntensity: 5000
};
```

## UniqueValueRenderer

```text
 renderer = {
  type: "unique-value",  // autocasts as new UniqueValueRenderer()
  field: "REGION",
  field2: "RANK",
  field3: "CLASS",
  fieldDelimiter: ", ",  // comma + space used to separate values from all fields
  uniqueValueInfos: [
    {
      value: "North, 1, medium",  // features in the "North" region, a rank of 1, and "medium" class
      symbol: sym1  // will be assigned sym1
    }, {
      value: "North, 2, medium",  // features in the "North" region, a rank of 2, and a "medium class
      symbol: sym2  // will be assigned sym2
    },
    ...
  ],
  visualVariables: [{
    type: "opacity",
    field: "POPULATION",
    normalizationField: "SQ_KM",
    // features with 30 ppl/sq km or below are assigned the first opacity value
    stops: [{ value: 100, opacity: 0.15 },
            { value: 1000, opacity: 0.90 }]
  }]
};

renderer.addUniqueValueInfo({

});
```

## ClassBreakRenderer

```text
renderer = {
  type: "class-breaks",  // autocasts as new ClassBreaksRenderer()
  field: "HARVESTED_ACRES",
  classBreakInfos: [
    {
      minValue: 0,  // 0 acres
      maxValue: 200000,  // 200,000 acres
      symbol: sym1,  // will be assigned sym1
      label: "fewer than 200,000 acres"
    }, {
      minValue: 200001,  // 200,001 acres
      maxValue: 500000,  // 500,000 acres
      symbol: sym2,  // will be assigned sym2
      label: "200,000 - 500,000 acres"
    }, {
      minValue: 500001,  // 500,001 acres
      maxValue: 750000,  // 750,000 acres
      symbol: sym3,  // will be assigned sym2
      label: "more than 500,000 acres"
    }
  ]
};

renderer.addClassBreakInfo({
  
});
```

## 

