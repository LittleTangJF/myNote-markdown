## 初始化

1、新建个盒子（宽高固定）

2、var myChart = echarts.init(ID) 初始化一个实例

3、myChart.setOption() 设置方法生成图表

## 图表样式

1、Theme 主题

1. ```js
   var chart = echarts.init(dom, 'light');
   ```

2、调色盘

1. ```js
   option = {
       // 全局调色盘。
       color: ['#c23531','#2f4554', '#61a0a8', '#d48265', '#91c7ae','#749f83',  '#ca8622', '#bda29a','#6e7074', '#546570', '#c4ccd3'],
   
       series: [{
           type: 'bar',
           // 此系列自己的调色盘。
           color: ['#dd6b66','#759aa0','#e69d87','#8dc1a9','#ea7e53','#eedd78','#73a373','#73b9bc','#7289ab', '#91ca8c','#f49f42'],
           ...
       }, {
           type: 'pie',
           // 此系列自己的调色盘。
           color: ['#37A2DA', '#32C5E9', '#67E0E3', '#9FE6B8', '#FFDB5C','#ff9f7f', '#fb7293', '#E062AE', '#E690D1', '#e7bcf3', '#9d96f5', '#8378EA', '#96BFFF'],
           ...
       }]
   }
   ```

   ### 3、直接的样式设置

   ### 	itemStyle, lineStyle, areaStyle, label,