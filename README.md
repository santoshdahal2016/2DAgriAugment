<p align="center" id="e-b">
<img src="https://gitee.com/_pure/codes/dn4u2bw65zxemfklcao9i45/raw?blob_name=vue-fabric.png" >
    <p align="center">
        <a href="https://opensource.org/licenses/artistic-license-2.0.php">
            <img src="https://img.shields.io/github/license/programmeres/easy-poi.svg" >
        </a>
        <a href="#e-b">
            <img src="https://img.shields.io/badge/coverage-100%25-red.svg" >
        </a>
        <a href="https://app.codacy.com/project/purestart/vue-fabric/dashboard">
            <img src="https://api.codacy.com/project/badge/Grade/90ac9cd605fe47dc835f0d571973e150" >
        </a>
         <a href="https://gitee.com/_pure/vue-fabric#project-donate-overview">
            <img src="https://img.shields.io/badge/donate-%EF%BF%A5-orange.svg" >
        </a>
    </p>    
</p>

# VueFabric

Forked from purestart's ![vue-fabric](https://github.com/purestart/vue-fabric).

<img src="https://gitee.com/_pure/codes/dn4u2bw65zxemfklcao9i45/raw?blob_name=fabric4.gif" >

## Installation

```
npm install vuejs-fabric --save
```

## Import

```
import VueFabric from 'vuejs-fabric';
```

```
Vue.component('VueFabric',VueFabric);
```

usa

```
 <vue-fabric ref="canvas" :width="width" :height="height"></vue-fabric>
```

## Usage

#### Props

| Name   | Type   | Default | Description   |
| ------ | ------ | ------- | ------------- |
| width  | Number | 0       | canvas width  |
| height | Number | 0       | canvas height |

## Function

> Method call
> this.\$refs.canvas.method(params)

#### createImage(url,options) 绘制图片

| params  | Type   | Description                                                                                                              |
| ------- | ------ | ------------------------------------------------------------------------------------------------------------------------ |
| url     | String | image url                                                                                                                |
| options | Object | id(DOM element ID),width,height,left,top,registeObjectEvent |

#### createTextbox(text,options) 绘制文本

| params  | Type   | Description                                |
| ------- | ------ | ------------------------------------------ |
| text    | String | text content                               |
| options | Object | width,left,top,fillColor(shape),fontSize,id |

#### createRect(options) 绘制矩形

| options   | Type   | Description    |
| --------- | ------ | -------------- |
| left      | Number | left           |
| top       | Number | top            |
| width     | Number | Rect width     |
| height    | Number | Rect height    |
| fillColor | String | Rect fillColor |
| id        | String | unique id    |

#### freeDrawConfig(options) 开启/关闭自由绘制（画笔）

| options       | Type    | Description                 |
| ------------- | ------- | --------------------------- |
| isDrawingMode | Boolean | Drawing true/false |
| color         | String  | Draw line color                  |
| drawWidth     | Number  | line width             |

#### createLine(options) 绘制直线

| options     | Type   | Description              |
| ----------- | ------ | ------------------------ |
| x,y,x1,y1   | Number | line points,直线两点坐标 |
| fillColor   | String | fillColor 填充颜色       |
| strokeColor | String | strokeColor 绘制颜色     |

#### drawDottedline(options) 绘制虚线

| options   | Type   | Description                               |
| --------- | ------ | ----------------------------------------- |
| x,y,x1,y1 | Number | line points,直线两点坐标                  |
| color     | String | 绘制线颜色                                |
| drawWidth | Number | 绘制线宽                                  |
| offset    | Number | 默认 6，每隔 offset 个像素空 empty 个像素 |
| empty     | Number | 默认 3，每隔 offset 个像素空 empty 个像素 |

#### drawArrowLine(options) 绘制箭头直线

| options   | Type   | Description              |
| --------- | ------ | ------------------------ |
| x,y,x1,y1 | Number | line points,直线两点坐标 |
| color     | String | 绘制线颜色               |
| drawWidth | Number | 绘制线宽                 |
| fillColor | Number | 默认透明，填充颜色       |
| theta     | Number | 默认 35，箭头角度大小    |
| headlen   | Number | 默认 35，箭头角度大小    |

#### createTriangle(options) 绘制三角形

| options         | Type   | Description         |
| --------------- | ------ | ------------------- |
| x,y,x1,y1,x2,y2 | Number | 三角形 3 点坐标位置 |
| left,top        | Number | position 位置       |
| color           | String | 绘制线颜色          |
| fillColor       | String | fillColor 填充颜色  |
| drawWidth       | Number | 绘制线宽            |

#### createEqualTriangle(options) 绘制等边三角形

| options  | Type   | Description        |
| -------- | ------ | ------------------ |
| left,top | Number | position 位置      |
| fill     | String | fillColor 填充颜色 |
| width    | Number | 三角形底边宽度     |
| height   | Number | 三角形高           |

#### createCircle(options) 绘制圆

| options  | Type   | Description        |
| -------- | ------ | ------------------ |
| left,top | Number | position 位置      |
| fill     | String | fillColor 填充颜色 |
| radius   | Number | 圆形半径           |

#### createEllipse(options) 绘制椭圆

| options     | Type   | Description                        |
| ----------- | ------ | ---------------------------------- |
| rx,ry       | Number | rx , ry 椭圆两个长轴尺寸和短轴尺寸 |
| left,top    | Number | position 位置                      |
| fillColor   | String | fillColor 填充颜色                 |
| strokeColor | String | strokeColor 绘制线颜色             |
| angle       | Number | angle 倾斜角度                     |

#### setRotate(angle) 旋转选中元素

| params | Type   | Description |
| ------ | ------ | ----------- |
| angle  | Number | 旋转角度    |

#### setBackgroundImage(url) 设置画布背景图片

| params | Type   | Description  |
| ------ | ------ | ------------ |
| url    | String | 背景图片 Url |

#### renderAll() 重新渲染画布

#### setBackgroundColor(color) 设置画布背景颜色

| params | Type   | Description |
| ------ | ------ | ----------- |
| color  | String | 背景颜色    |

#### toggleMirror(options) 设置图片元素镜像翻转

| options | Type   | Description                         |
| ------- | ------ | ----------------------------------- |
| flip    | String | 可选值 X,Y 默认值 X , 镜像翻转 X，Y |

#### setCornerIcons(options) 自定义旋转操作元素图片

| options               | Type   | Description                                                   |
| --------------------- | ------ | ------------------------------------------------------------- |
| size                  | Npmber | 图片大小 px                                                   |
| borderColor           | String | 图片边框颜色                                                  |
| cornerBackgroundColor | String | 设置背景颜色                                                  |
| cornerShape           | String | 形状，默认'rect' ，可选'rect', 'circle'                       |
| tl                    | String | top left 左上角元素图片地址（本地只能 static 下的图片）       |
| tr                    | String | top right 右上角元素图片地址（本地只能 static 下的图片）      |
| bl                    | String | bottom left 左下角元素图片地址（本地只能 static 下的图片）    |
| br                    | String | bottom right 右下角元素图片地址（本地只能 static 下的图片）   |
| ml                    | String | middle left 中间左边元素图片地址（本地只能 static 下的图片）  |
| mr                    | String | middle right 中间右边元素图片地址（本地只能 static 下的图片） |
| mtr                   | String | middle top 顶部元素图片地址（本地只能 static 下的图片）       |

#### toNextLayer() 设置当前选中画布到下一层

#### toLastLayer() 设置当前选中画布到上一层

#### toBottomLayer() 设置当前选中画布到底层

#### toTopLayer() 设置当前选中画布到顶层

#### discardActive() 取消选中

#### getObjects() 获取当前画布上的所有元素对象

#### clear() 清除当前画布上的所有元素对象

#### toDataUrl() 返回当前画布的 base64 图片

#### toJson() 返回当前画布的 json 对象

#### loadFromJSON(json,cb) 从 json 对象中加载画布数据

| params | Type     | Description      |
| ------ | -------- | ---------------- |
| json   | Object   | json 对象        |
| cb     | Function | 加载完成回调函数 |

#### toSvg() 返回当前画布的 svg 图片

#### removeCurrentObj() 删除当前选中对象

#### getEditObj() 返回当前选中对象，并不在画布上显示，用于编辑当前元素

#### setEditObj(obj) 设置添加对象到画布

## 事件

```
 <vue-fabric ref="canvas" @selection:created="selected" :width="width" :height="height"></vue-fabric>
```

Mouse event

| name           | Type  | Description    |
| -------------- | ----- | -------------- |
| mouse:down     | event | mouse down     |
| mouse:up       | event | mouse up       |
| mouse:move     | event | mouse move     |
| mouse:dblclick | event | mouse dblclick |
| mouse:over     | event | mouse over     |
| mouse:out      | event | mouse out      |

Other events

| name                     | Type  | Description                                    |
| ------------------------ | ----- | ---------------------------------------------- |
| selection:created        | event | 选中 canvas 元素对象，单选和多选都会触发此事件 |
| selection:updated        | event | selection updated                              |
| selection:cleared        | event | selection cleared                              |
| before:selection:cleared | event | before selection cleared                       |
| object:added             | event | 当有元素被添加进来时候触发                     |
| object:removed           | event | object removed                                 |
| object:modified          | event | object modified                                |
| object:rotating          | event | object rotating                                |
| object:scaling           | event | object scaling                                 |
| object:moving            | event | object moving                                  |