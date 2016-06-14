#canvas常用API

##形状

> 矩形

* ctx.fillRect();    填充
  fillRect(x, y, width, height)
* ctx.strokeRect();  描边
* ctx.clearRect();  画布特点，绘制上的元素无法更改 
 
  2种方法清除 1.重新设置为原来的宽高  2.clearRect（）
  document.onclick = function(){
    canvas.width() = canvas.height() = 600,
    ctx.clearRect(0,0,600,600);
  }


> 圆

* ctx.arc();     圆
  arc(x, y, radius, startAngle, endAngle, anticlockwise)
  arc()函数中的角度单位是弧度，不是度数。角度与弧度的js表达式:radians=(Math.PI/180)*degrees。
* ctx.arcTo();   圆弧  不常用
  arcTo(x1, y1, x2, y2, radius)

> 线
*ctx.beginPath();     开始一个路径
*ctx.moveTo();        移动画笔到某个点
*ctx.lineTo();        让路径中拥有条到某点的线，并不是画
*ctx.rect()           拥有一个矩形
*ctx.fill()           填充当前路径
*ctx.stroke();        描边当前路径
*ctx.clearRect();     清除矩形区域
*ctx.closePath();     结束一个路径


二次贝塞尔
*ctx.quadraticCurveTo(cp1x, cp1y, x, y)
 x,y为结束点，cp1x,cp1y为控制点
三次贝塞尔
*ctx.bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
 x,y为结束点，cp1x,cp1y为控制点一，cp2x,cp2y为控制点二


##样式
ctx.fillStyle = color 图形的填充颜色 color 可以是表示 CSS 颜色值的字符串，渐变对象或者图案对象
ctx.strokeStyle = color 图形轮廓的颜色
ctx.globalAlpha = transparencyValue 有效的值范围是 0.0 （完全透明）到 1.0（完全不透明），默认是 1.0

ctx.lineWidth = value 设置线条宽度
ctx.lineCap = type 设置线条末端样式  butt，round 和 square。默认是 butt
ctx.lineJoin = type 设定线条与线条间接合处的样式 round, bevel 和 miter。默认是 miter
ctx.miterLimit = value限制当两条线相交时交接处最大长度；所谓交接处长度是指线条交接处内角顶点到外角顶点的长度
ctx.getLineDash() 返回一个包含当前虚线样式，长度为非负偶数的数组
ctx.setLineDash(segments) 设置当前虚线样式
ctx.lineDashOffset = value 设置虚线样式的起始偏移量

ctx.createLinearGradient(x1, y1, x2, y2) 方法接受 4 个参数，表示渐变的起点 (x1,y1) 与终点 (x2,y2)
ctx.createRadialGradient(x1, y1, r1, x2, y2, r2) 
6个参数，前三个定义一个以 (x1,y1) 为原点，半径为 r1 的圆，后三个定义另一个以 (x2,y2) 为原点，半径为 r2 的圆
createPattern(image, type)
  Image 可以是一个 Image 对象的引用，或者另一个 canvas 对象。
  Type 必须是下面的字符串值之一：repeat，repeat-x，repeat-y 和 no-repeat

 1. window.onload = function(){
      var img = document.querySelector('#img');
      var xxx = ctx.createPattern(img,'no-repeat');
      ctx.fillstyle = xxx;
    }
 2. var img = new Image();
	   img.src = '01.jpg'; 
	   img.onload = function(){        //$(img).on('load',function(){})
		   var imgs = ctx.createPattern(img,'no-repeat');
		   ctx.fillStyle = imgs;
		   ctx.fillRect(0,0,1000,1000)
	  }



shadowOffsetX = float 设定阴影在 X 和 Y 轴的延伸距 。负值表示阴影会往上或左延伸，正值则表示会往下或右延伸
shadowOffsetY = float
shadowBlur = float 设定阴影的模糊程度，其数值并不跟像素数量挂钩
shadowColor = color 用于设定阴影颜色效果 默认是全透明的黑色


##位移 (挪动画布)
只会保存画布状态，不保存任何图像
ctx.save();
ctx.restore();


ctx.translate(x,y);
ctx.rotate((Math.PI/180)*30);
ctx.scale();



画布特点：
1.清除
2.重绘

var now = new Date();
now.getHours()
now.getMinutes()
now.getseconds()


## 文本
font = '10px Arial';
ctx.textAlign = 'right'
ctx.font = '58px Arial';
ctx.strokeText('Hello',0,300);  
ctx.shadowOffsetY = 10;
ctx.shadowOffsetX=10;
ctx.shadowBlur = 3;
ctx.shadowColor = black;s

var I = new Image();
i.src = ''
ctx.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)
第一个参数和其它的是相同的，都是一个图像或者另一个 canvas 的引用。其它8个参数最好是参照右边的图解，前4个是定义图像源的切片位置和大小，后4个则是定义切片的目标显示位置和大小
ctx.drawImage(document.getElementById('source'),
                33,71,104,124,21,20,87,104)
