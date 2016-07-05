# index.html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
<style>
    .content{
        margin-top: 10px;
        border-bottom: 1px solid darkseagreen;

    }
    .content:nth-child(1) h3{
        color: rebeccapurple;
    }
    .content:nth-child(2) h3{
        color: aquamarine;
    }
    .content:nth-child(3) h3{
        color: #703210;
    }
    .content:nth-child(4) h3{
        color: greenyellow;
    }
    .article-title{
        font-size:26px;
        font-weight: bolder;
        border:1px dashed darkorchid;
    }

</style>
<div class="container">
    <section>
        <nav>
            <ul class="nav-header">
                <li class="cur">首页</li>
                <li>全部商品</li>
                <li>最新上架</li>
                <li>3C热销</li>
                <li>最新优惠</li>
            </ul>
            <!--href="javascript:void(0)禁用a标签的跳转 常用技巧-->
            <a href="javascript:void(0)" id="btn">登入</a>
            <a href="javascript:void(0)" id="btn">注册</a>
        </nav>
    </section>
    <div class="main">
        <div class="content">
            <ul class="articles">
                <h3>XX系列</h3>
                <li class="article-item">文章1-1</li>
                <li class="article-item">文章1-2</li>
                <li class="article-item">文章1-3</li>
                <li class="article-item">文章1-4</li>
                <li class="article-item">文章1-5</li>
            </ul>
        </div>
        <div class="content">
            <ul class="articles">
                <h3>YY系列</h3>
                <li class="article-item">文章2-1</li>
                <li class="article-item">文章2-2</li>
                <li class="article-item">文章2-3</li>
                <li class="article-item">文章2-4</li>
                <li class="article-item">文章2-5</li>
            </ul>
        </div>
        <div class="content">
            <ul class="articles">
                <h3>QQ系列</h3>
                <li class="article-item">文章3-1</li>
                <li class="article-item">文章3-2</li>
                <li class="article-item">文章3-3</li>
                <li class="article-item">文章3-4</li>
                <li class="article-item">文章3-5</li>
            </ul>
        </div>
        <div class="content">
            <ul class="articles">
                <h3>PP系列</h3>
                <li class="article-item">文章4-1</li>
                <li class="article-item">文章4-2</li>
                <li class="article-item">文章4-3</li>
                <li class="article-item">文章4-4</li>
                <li class="article-item">文章4-5</li>
            </ul>
        </div>
    </div>
</div>
<script src="node_modules/jquery/dist/jquery.js"></script>
<script src="js/index.js"></script>
</body>
</html>
```

```javascript
//此为jQuery的常用标准写法
//在页面中的Html元素加载完成后执行方法体内的内容
$(function(){
/**当页面html中存在两个id相同的元素时
    我们通过元素选择器获得的是第一个元素
    对元素添加时间的时候,也只有第一个元素的效果*/
    console.log($("btn")).text());
    $("#btn").click(function(){ alert($(this).text);})
    
    //选中class = "cur"标签
    $(".cur")//1
    $(".nav=header .cur")//2
    $("nav .cur")//3
    $(".nav-header").find(".cur")//在选中元素的基础上查找
    
    //通过eq选中指定索引的位置的元素
    $(".nav-header" li).eq(2);//选中第三个Li元素.eq选中指定索引位置(从0开始)的元素
    
    //选中class="nav-header"的标签的所有子级
    $("section").childern();//包含标签内部的所有子级(即标签的所有子级)(nav)
    $("section").parents();//返回的结果为所有的父级.
    $("section").parent();//返回所有丶父级避免使用此方法
    
    //对对象进行后续操作 是Js中常见的写法
    $(".nav-header").find(".cur")siblings().css("color","red")//查找同一级的所有元素
    $(".nav-header").find(".cur").next().css("color","blue")//找到和自己同级的下一个元素
    $(".nav-header").find(".cur").text();//获取.cur标签内的文本字段
    $(".nav-header").find(".cur").wrap();//获取.cur标签跟内容
    
    $(".nav-header li").eq("3").prev();//prev查找紧挨直接的上一个同级元素
    $(".nav-header").find(".cur").nextAll();//查找同级的紧挨直接的后续元素
    $(".nav-header li").eq("3").prevAll().text('我是第四个元素的前面的元素')//查找同级的紧挨自己的前面的元素
    
    $(".content").each(function(){
    //设置当前div的color值为 当前div中h3标签的color值
        $(this).css("color",$(this).find("h3").css("color"));

        //添加多个css样式的写法
        //$(this).css({
        //    "font-size":"24px",
        //    "text-align":"center"
        //});
        var text = $(this).find("h3").text();//获取当前div中的h3文本内容
        //遍历div中的class="article-item"的元素 进行循环赋值.
        $(this).find('.article-item').each(function(index){
            $(this).text(text+(index+1));
        })
    })
    //$(".article-item").addClass('article-title');//添加样式

    //$(".article-item").removeClass('article-title');//删除样式

    $(window).width()//获取窗口宽
    $(window).height()//获取窗口高

    //监听窗口大小改变的时间
    $(window).resize(function(){
        console.log('window is changing size...');
        console.log('width:'+$(window).width());
        console.log('height:'+$(window).height());
    })
})

```
