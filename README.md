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

在线页面上挂载了这个插件的演示示例： [点击查看演示！](https://react-map.github.io/leaflet.migrationLayer/).

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

##API(选项)  

| 选项            | 描述                    | 默认值           | 类型                    | 是否必须       |
| --------------- | ---------------------- | -----------------| ------------------------ | -------------- | 
| map             | 地图对象                | null             | Map                      | yes             |
| data            | 图层数据                | null             | Json                     | yes            | 
| pulseRadius     | 脉冲半径                | 25               | any number>0             | no             |
| pulseBorderWidth| 脉冲边界宽度            | 3                | any number>0             | no             |
| arcWidth        | 弧宽                    | 1                | any number>0             | no             |
| arcLabel        | 是否显示起始标签         | true             | Bool                     | no             |
| arcLabelFont    | 标签文字字体和大小       | '15px sans-serif'| 'size font'              | no             |   

## Leaflet 版本     
要求 Leaflet 1.0.2 或者更新的版本   

## 许可 
MIT.    
