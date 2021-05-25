# CSS笔记

CSS引入方式

1. 外部样式表   （就是用link标签引入的css文件）

```html
<link rel="stylesheet" href="./xxx.css" />
```

2. 内联样式表   （在head标签里用style标签包裹的css样式）

​```html
<head>
    <style>
        div {
            background:red;
        }

    </style>
</head>
```
3. 行内样式      （就是在标签内添加style属性，值就是css样式）

​```html
    <div style="background:red;"></div>
```








## 定位

定位有四种

- 相对定位 relative
    - 相对于它自己进行定位
- 绝对定位 absolute
    - 相对于祖先元素不是static定位的元素进行定位，如果祖先元素都是static,那就相对于浏览器进行定位
- 固定定位 fixed
    - 始终相对于浏览器进行定位
- 默认定位 static
    - 默认定位（不写定位就是它）


## 动画  animate

@keyframes  定义一个动画

给元素添加animation相关属性应用动画
animation-name  动画的名字
animation-duration 动画持续时间
animation-timing-function 指定动画的速度曲线
animation-iteration-count 动画的播放次数
animation-direction 规定动画是否在下一周期逆向地播放



## 阴影

box-shadow：h-shadow    v-shadow   v-shadow    blur    spread    color    inset


值	说明
h-shadow	必需的。水平阴影的位置。允许负值
v-shadow	必需的。垂直阴影的位置。允许负值
blur	可选。模糊距离
spread	可选。阴影的大小
color	可选。阴影的颜色。在CSS颜色值寻找颜色值的完整列表
inset	可选。从外层的阴影（开始时）改变阴影内侧阴影