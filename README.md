# 教学文档  
## 1.引入文件 
```
<link rel="stylesheet" href="./css/table.css">
<link rel="stylesheet" href="./scroll_bar_fonts/iconfont.css">
<script src="./js/jquery-1.11.1.js"></script>
<script src="./js/move.js"></script>
<script src="./js/table.js"></script>
```

## 2.html基础结构图
![图片名称](https://github.com/laoa1717/img-store/blob/master/pc-table-img/%E5%9B%BE%E7%89%871.png?raw=true)  

### 2.1  表格头部固定区域scroll-table-head
```html
<!-- 表格头部固定区域 -->
<div class="scroll-table-head">
  <table class="tb1 tb2">
    <thead>
      <tr>
        <!-- <th style="width: 宽度自行定制(必填);">...</th> 例子如下-->
        <th style="width: 9em;">头部1</th>
        <th style="width: 8em;">头部2</th>
        ............
      </tr>
    </thead>
  </table>
</div>
```

### 2.2  表格主体区域scroll-table-body
```html
<!-- 表格主体区域 -->
<div class="scroll-table-body">
    <table class="tb1 tb2">
        <thead>
            <tr>
                <!-- <th style="width: 宽度自行定制(必填);">...</th> 例子如下-->
                <!-- 和上面的表格头部固定区域保持一致-->
                <th style="width: 9em;">头部1</th>
                <th style="width: 8em;">头部2</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <!-- data-name="和头部的名称保持一致" -->
                <td data-name="头部1">
                    <!-- 内容外层要包class="td_div"的div层 -->
                    <div class="td_div">...</div>
                </td>
                <td data-name="头部2">
                    <!-- 特殊情况,如果里层是input输入框或者a标签,需要加fix_tab的class -->
                    <div class="td_div fix_tab">
                        <input type="text"> <!-- 或者<a>...</a> -->
                    </div>
                </td>
            </tr>
            <tr>...</tr>
            <tr>...</tr>
        </tbody>
    </table>
    <!-- 表格自定义垂直滚动条 -->
    <!-- 以EC为例,没数据的时候不显示滚动条,所以加了c:if判断 -->
    <c:if test="${resList.size()>0}">
        <div class="v-scroll-bar-box">
            <div class="up-arrow">
                <i class="iconfont icon-shangjiantoushixinxiao arrow"></i>
            </div>
            <div class="v-scroll-bar"></div>
            <div class="down-arrow">
                <i class="iconfont icon-xiajiantoushixinxiao arrow"></i>
            </div>
        </div>
    </c:if>
</div>
```  

### 2.3  表格侧边栏固定区域scroll-table-fixed-left
```html
<!-- 表格侧边栏固定区域 -->
<div class="scroll-table-fixed-left hide">
    <!-- 表格侧边栏head区域 -->
    <div class="scroll-table-fixed-left-head">
        <table class="tb1 tb2 no_border_bottom">
            <thead>
                <tr>
                    <!-- <th style="width: 宽度自行定制(必填);">...</th> 例子如下-->
                    <!-- 和上面的表格头部固定区域保持一致-->
                    <!-- 要固定左边几列就写几个th -->
                    <th style="width: 9em;">头部1</th>
                    <th style="width: 8em;">头部2</th>
                </tr>
            </thead>
        </table>
    </div>
    <!-- 表格侧边栏body区域 -->
    <div class="scroll-table-fixed-left-body">
        <table class="tb1 tb2">
            <tbody>
                <tr>
                    <td style="width: 9em;" data-name="头部1">
                        <div class="td_div">...</div>
                    </td>
                    <!-- 有几列就写几个td的数据 -->
                    <td style="width: 8em;" data-name="头部2">...</td>
                    <td>...</td>
                </tr>
                <tr>...</tr>
                <tr>...</tr>
            </tbody>
        </table>
    </div>
</div>
<!-- 表格自定义横向滚动条 -->
<c:if test="${resList.size()>0}">
    <div class="scroll-bar-box">
        <div class="left-arrow">
            <i class="iconfont icon-zuojiantoushixinxiao arrow"></i>
        </div>
        <div class="scroll-bar"></div>
        <div class="right-arrow">
            <i class="iconfont icon-youjiantoushixinxiao arrow"></i>
        </div>
    </div>
</c:if>
```

## 3.script调用脚本
***复合型 thead***
![图片名称](https://github.com/laoa1717/img-store/blob/master/pc-table-img/%E5%9B%BE%E7%89%873.png?raw=true)
***非复合型 thead***
![图片名称](https://github.com/laoa1717/img-store/blob/master/pc-table-img/%E5%9B%BE%E7%89%872.png?raw=true)
```js
$(function () {
    /*固定表格滑动脚本*/
    var fixThead = false; // 是否为复合型thead
    tableSwiperFunc({
        wrap_body: $(".scroll-table-body")[0],
        scroll_body: $(".scroll-table-body table")[0],
        wrap_head: $(".scroll-table-head")[0],
        scroll_head: $(".scroll-table-head table")[0],
        left_wrap_body: $(".scroll-table-fixed-left-body")[0],
        left_scroll_body: $(".scroll-table-fixed-left-body table")[0],
        horizontal_bar: $('.scroll-bar')[0],
        vertical_bar: $('.v-scroll-bar')[0]
    });
    calcRowHeight(fixThead);
})

/*ec碰到的特殊情况*/
showLoadingDialog("正在查询");
setTimeout(function(){
	var fixThead = true; //是否为复合型thead
	tableSwiperFunc({
		wrap_body: $(".scroll-table-body")[0],
		scroll_body: $(".scroll-table-body table")[0],
		wrap_head: $(".scroll-table-head")[0],
		scroll_head: $(".scroll-table-head table")[0],
		left_wrap_body: $(".scroll-table-fixed-left-body")[0],
		left_scroll_body: $(".scroll-table-fixed-left-body table")[0],
		horizontal_bar: $('.scroll-bar')[0],
		vertical_bar: $('.v-scroll-bar')[0],
	});
	calcRowHeight(fixThead);
	hideLoadingDialog();
},500);
```







