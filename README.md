# leaflet.migrationLayer

leafet.migrationLayer 是用来展示迁徙数据的图层，迁徙数据包括人口、交通、航行、空运等等。这是一种地图数据可视化方法。
<div style="text-align:center" align="center">
  <img src="https://react-map.github.io/leaflet.migrationLayer/demo.gif" />
</div>     

## 支持浏览器

IE浏览器10以上版本
谷歌浏览器  
Safari 浏览器   
火狐浏览器        

## 在线演示

在线页面上挂载了这个插件的演示示例： [点击查看演示！](https://react-map.github.io/leaflet.migrationLayer/)。

## 用法    

1. 包含位于 ```\dist``` 目录下的JavaScript文件
```html
<script src="./dist/leaflet.migrationLayer.js"></script>
```    
2. 新建一个飞线图层
```js
var migrationLayer = new L.migrationLayer({
    map: map,
    data: data
})
```     
3. 给这个图层设置或更新数据
```js
migrationLayer.setData(newData);
```   
4. 隐藏图层 
```js
migrationLayer.hide();
```   
5. 显示图层 
```js
migrationLayer.show();
```   
6. 暂停动画
```js
migrationLayer.pause();
```   
7. 开始动画
```js
migrationLayer.play();
```   
8. 销毁图层 
```js
migrationLayer.destroy();
```   

## API(选项)  

| 选项            | 描述                    | 默认值           | 类型                    | 是否必须       |
| --------------- | ---------------------- | -----------------| ------------------------ | -------------- | 
| map             | 地图对象                | null             | Map                      | yes             |
| data            | 图层数据                | null             | Json                     | yes            | 
| pulseRadius     | 脉冲半径                | 25               | any number>0             | no             |
| pulseBorderWidth| 脉冲边界宽度            | 3                | any number>0             | no             |
| arcWidth        | 弧宽                    | 1                | any number>0             | no             |
| arcLabel        | 是否显示起始标签         | true             | Bool                     | no             |
| arcLabelFont    | 标签文字字体和大小       | '15px sans-serif'| 'size font'              | no             |   

## 数据格式

此插件接入数据为JSON格式，具体格式如下：

`[{"from":[<long>,<lat>],"to":[<long>,<lat>],"labels":[<起点文本>,<终点文本>],"color":<颜色值>},{...},...]`

每一条飞线都有如下参数：

| 参数   | 描述                                            | 类型      |
| ------ | ---------------------------------------------- | --------- |
| from   | 起点经纬度坐标，格式为`[<经度>，<纬度>]`          | JSON数组  |
| to     | 终点经纬度坐标，格式为`[<经度>，<纬度>]`          | JSON数组  |
| labels | 飞线两端点文本，格式为`[<起点文本>,<终点文本>]`    | JSON数组  |
| color  | 飞线颜色，可以是十六进制颜色值或rgb(a)、hsl颜色值  | 颜色值    |

## 示例代码

```html
<head>
    <meta charset="UTF-8">
    <title>Migration Layer</title>
    <link rel="stylesheet" href="./lib/leaflet.css" />
    <style>
    html,body{
        margin: 0;
        padding: 0;
    }
    #map{
        position: absolute;
        height: 100%;
        width: 100%;
    }
    #event{
        position: absolute;
        top: 50px;
        right: 600px;
        height: 100px;
        width: 400px;
        z-index: 10000;
    }
    .btn{
        border-color:gray;
        border-width: 2px;
        background-color:white;
   }
    </style>
</head>
<body>
    <div id="map"></div>
    <div id='event'>
        <input type="button" value="setData" class="btn" onclick="setData()">
        <input type="button" value="hide" class="btn" onclick="hide()">
        <input type="button" value="show" class="btn" onclick="show()">
        <input type="button" value="pause" class="btn" onclick="pause()">
        <input type="button" value="play" class="btn" onclick="play()">
        <input type="button" value="destroy" class="btn" onclick="destroy()">
    </div>
    <script src="./lib/leaflet.js"></script>
    <script src='./dist/leaflet.migrationLayer.js'></script>
    <script>
        var lrmap = L.map('map').setView([35, -95], 5);
        L.tileLayer('https://api.tiles.mapbox.com/v4/mapbox.dark/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw')
        .addTo(lrmap);

        var data = [{"from":[-118.2705,33.9984],"to":[-122.789336,37.920458],"labels":["Los Angeles","San Francisco"],"color":"#ff3a31"},{"from":[-118.2705,33.9984],"to":[-80.247887,25.792296],"labels":[null,"Miami"],"color":"#ff7e2b"},{"from":[-118.2705,33.9984],"to":[-73.999705,40.795047],"labels":[null,"New York"],"color":"#ffc726"},{"from":[-118.2705,33.9984],"to":[-87.724088,41.917846],"labels":[null,"Chicago"],"color":"#e9ff20"},{"from":[-118.2705,33.9984],"to":[-92.145189,46.77372],"labels":[null,"Duluth"],"color":"#99ff1b"},{"from":[-118.2705,33.9984],"to":[-111.824547,40.788055],"labels":[null,"Salt Lake"],"color":"#45ff15"},{"from":[-118.2705,33.9984],"to":[-111.364615,47.536109],"labels":[null,"Great Falls"],"color":"#10ff33"},{"from":[-118.2705,33.9984],"to":[-97.585039,35.511099],"labels":[null,"Oklahoma"],"color":"#0aff84"},{"from":[-118.2705,33.9984],"to":[-115.157907,36.173032],"labels":[null,"Las Vegas"],"color":"#05ffd9"},{"from":[-118.2705,33.9984],"to":[-103.196215,34.418753],"labels":[null,"Clovis"],"color":"#00ccff"}];
        
        var data2=[{"from":[-73.875523,40.781063],"to":[-80.247887,25.792296],"labels":["New York","Maima"],"color":"#05ffd9"},{"from":[-73.875523,40.781063],"to":[-118.2705,33.9984],"labels":[null,"Los Angeles"],"color":"#00ccff"},{"from":[-73.875523,40.781063],"to":[-87.724088,41.917846],"labels":[null,"Chicago"],"color":"#ffc726"},{"from":[-73.875523,40.781063],"to":[-71.058437,42.35902],"labels":[null,"Boston"],"color":"#e9ff20"},{"from":[-73.875523,40.781063],"to":[-75.683057,45.42172],"labels":[null,"Ottawa"],"color":"#99ff1b"}];

        var migrationLayer = new L.migrationLayer({
            map: lrmap,
            data: data,
            pulseRadius:30,
            pulseBorderWidth:3,
            arcWidth:1,
            arcLabel:true,
            arcLabelFont:'10px sans-serif',
            }
        );
        migrationLayer.addTo(lrmap);

        function setData(){
            migrationLayer.setData(data2);
        }
        function hide(){
            migrationLayer.hide();
        }
        function show(){
            migrationLayer.show();
        }
        function play(){
            migrationLayer.play();
        }
        function pause(){
            migrationLayer.pause();
        }
        function destroy() {
            migrationLayer.destroy();
        }
    </script>
</body>
```
## Leaflet 版本     
要求 Leaflet 1.0.2 或者更新的版本   

## 许可 
MIT.    
