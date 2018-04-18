# knowledge_point_summary
总结一些自己开发中遇到的问题

两个行块宽度50%却不在同一行（设置了inline或者inline-block属性）
例如：
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            padding:0;
            margin: 0;
            border: none;
        }
        .wrapper {
            width: 500px;
            overflow: hidden;
            background-color: grey;
        }
        .cell {
            display: inline-block;
            width: 50%;
        }
        .left {
            background-color: red;
        }
        .right{
            background-color: blue;
            
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="cell left">left</div>
        <div class="cell right">right</div>
    </div>
</body>
</html>
```
答：inline和inline-block是内联布局，既然是内联那么就会受空白区域的影响，两个子div之间有一个 空白文本节点！去掉后就好了。

1)可以设置.wrapper的font-size为0，再在子div上设置字体大小就可以了。

2）设置父容器和子元素为浮动
```css
.wrapper {
    width: 500px;
    overflow: hidden;
    background-color: grey;
    font-size: 0;
}
.cell {
    display: inline-block;
    width: 50%;
    font-size:12px;
}
```
