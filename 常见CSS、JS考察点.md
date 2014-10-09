#经常考察的css和js概念
---
##CSS
###BFC
####概念
块级格式化上下文，它是指一个独立的块级渲染区域，只有Block-level BOX参与，该区域拥有一套渲染规则来约束块级盒子的布局，且与区域外部无关。
####使用条件
根元素:body
float的值不为none
overflow的值不为visible
display的值为inline-block、table-cell、table-caption
position的值为absolute或fixed
####约束规则
内部的Box会在垂直方向上一个接一个的放置
垂直方向上的距离由margin决定。（完整的说法是：属于同一个BFC的两个相邻Box的margin会发生重叠，与方向无关。）
每个元素的左外边距与包含块的左边界相接触（从左向右），即使浮动元素也是如此。（这说明BFC中子元素不会超出他的包含块，而position为absolute的元素可以超出他的包含块边界）
BFC的区域不会与float的元素区域重叠
计算BFC的高度时，浮动子元素也参与计算
BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面元素，反之亦然
####作用
#####防止margin重叠
当一个容器既没有border又没有padding时，它的第一个子box的的margin也能跟它的上一个容器的margin发生叠加，所以在这个需要防止重叠margin的子元素的父元素创建一个bfc
#####父元素高度自适应子元素
常见场景ul包含若干个li，li的内容不能顶开ul的高度，这个时候创建一个ul的bfc，就可以解决
#####自适应布局
在定宽的浮动元素旁建立一个bfc，即可实现两栏自适应布局

###haslayout
####概念
对于并非所有的元素都默认有布局，微软给出的主要原因是“性能和简洁”。如果所有的元素都默认有布局，会对性能和内存使用上产生有害的影响。大部分的 IE 显示错误，都可以通过激发元素的 haslayout 属性来修正。可以通过设置 css 尺寸属性(width/height)等来激发元素的 haslayout，使其“拥有布局”。如下所示，通过设置以下 css 属性即可。
####使用条件
display: inline-block
height: (任何值除了auto)
float: (left 或 right)
position: absolute
width: (任何值除了auto)
writing-mode: tb-rl
zoom: (除 normal 外任意值) 

IE7还有额外的方法
min-height: (任意值)
max-height: (除 none 外任意值)
min-width: (任意值)
max-width: (除 none 外任意值)
overflow: (除 visible 外任意值)
overflow-x: (除 visible 外任意值)
overflow-y: (除 visible 外任意值)
position: fixed
####作用
具有“layout” 的元素如果同时 display: inline ，那么它的行为就和标准中所说的 inline-block 很类似了：在段落中和普通文字一样在水平方向和连续排列，受 vertical-align 影响，并且大小可以根据内容自适应调整。这也可以解释为什么单单在 IE/Win 中内联元素可以包含块级元素而少出问题，因为在别的浏览器中 display: inline 就是内联，不像 IE/Win 一旦内联元素拥有 layout 还会变成 inline-block。

###寂寞的垂直居中
####transform:translateY(-50%)
#####Talk is cheap show me the code
    .dialog{
        position:absolute;
        top:50%;
        transform:translateY(-50%);
    }
    <body>
        <div class="dialog"></div>
    </body>
#####兼容性和场景
    结构很简洁
    IE9+ 支持css3的浏览器
    用于手机开发做一个弹窗或文字图片居中

####百分比布局和负margin
#####Talk is cheap show me the code
    .dialog{
        position:absolute;
        top:50%;
        left:50%;
        margin-left:-100px;
        margin-top:-100px;
        width:200px;
        height:200px;
    }
    <body>
        <div class="dialog"></div>
    </body>
#####兼容性和场景
    结构很简洁、必须知道宽高，兼容IE6
    各种寂寞的弹窗必用

####display: table-cell
#####Talk is cheap show me the code
    html,body{
        height:100%;
    }
    .middle{
        display:table-cell;
        height:90px;
        vertical-align: middle;
    }
    <body>
        <div class="middle"><img src="" alt=""></div>
    </body>
#####兼容性和场景
    IE8+ 
    由于容器高度固定，设置overflow: hidden 会导致文字不显示
    和文字撑开兄弟元素不居中
    所以仅用于文字居中的情况或图片居中
    配合下面的font-size用法兼容IE6、7


####ie6、7 font-size为高度的0.873倍
#####Talk is cheap show me the code
    html,body{
        height:100%;
    }
    .middle{
        text-align:center;
        display:table-cell;
        height:90px;
        vertical-align: middle;
        *display:block;
        *font-size:175px;
    }
    .middle img{
        verical-align:middle;
    }
    <body>
        <div class="middle"><img src="" alt=""></div>
    </body>
#####兼容性和场景
    这个方法好像是IE6下标签最简单的图片的垂直居中的方法了


####三层div法 第二层top:50% 第三层top:-50%
#####Talk is cheap show me the code
    .wrap {
        width: 300px;
        height: 300px;
        border: 3px solid #ddd;
        display: table;
        *position: relative;
    }
    .hack {
        display: table-cell;
        vertical-align: middle;
        *position: absolute;
        *top: 50%;
    }
    .cnt {
        *position: relative;
        *top: -50%;
    }
    <div class="wrap">
        <div class="hack">
            <div class="cnt">
                <img src="http://pic002.cnblogs.com/images/2012/382256/2012080118323766.gif" width="50%">
            </div>
        </div>
    </div>

#####兼容性和场景
    IE6+
    这种方法多了一层无语义的div

##JS
###闭包
####概念
当一个内部函数被调用，函数中有使用到局部变量，就会形成闭包。
####使用场景
#####建立一个单例环境
            
    var singleton = function( fn ){
        var result;
        return function(){
            return result || ( result = fn .apply( this, arguments ) );
        }
    }
    var createMask = singleton( function(){
        return document.body.appendChild( document.createElement('div') );         
    })

#####循环绑定事件的变量取值
    for (var i = 0; i < menuLi.length; i++) {
        var num = i;
        menuLi[i].onclick = (function(_num) {
            return function(){
                console.log(menuContent[_num]);
                console.log(menuContent[_num].className);
            }

        })(num)
    }
