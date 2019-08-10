# 教学文档  
***效果请看 --->PC端表格组件 / table.html***
## 1.引入文件 
```
<link rel="stylesheet" href="./css/table.css">
<link rel="stylesheet" href="./scroll_bar_fonts/iconfont.css">
<script src="./js/jquery-1.11.1.js"></script>
<script src="./js/move.js"></script>
<script src="./js/table.js"></script>
```

## 2.HTML结构
```html
<div class="scroll-table-box">
	<!-- 表格主体区域 -->
	<div class="scroll-table-body">
	    <table class="tb1 tb2">
		<thead>
		    <tr>
			<!-- <th style="width: 宽度自行定制(必填);">...</th> 例子如下-->
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
	</div>
</div>
```

## 3.script调用脚本
***复合型 thead***
![图片名称](https://github.com/laoa1717/img-store/blob/master/pc-table-img/%E5%9B%BE%E7%89%873.png?raw=true)
***非复合型 thead***
![图片名称](https://github.com/laoa1717/img-store/blob/master/pc-table-img/%E5%9B%BE%E7%89%872.png?raw=true)
```js
$(function () {
	/*固定表格滑动脚本*/
	initTable({
		colNum: 4,//左边固定的列数,默认为0
		maxHeight: 400,//可视区最大高度,默认400px,低于200px按200px计算
		fixThead: false,// 是否为复合型thead,默认为false
	});
})

/*ec碰到的特殊情况,此情况发生于页面后台数据还没传过来,表格脚本就执行了,导致表格脚本执行混乱*/
showLoadingDialog("正在查询");
setTimeout(function(){
	/*固定表格滑动脚本*/
	initTable({
		colNum: 4,//左边固定的列数,默认为0
		maxHeight: 400,//可视区最大高度,默认400px,低于200px按200px计算
		fixThead: false,// 是否为复合型thead,默认为false
	});
	hideLoadingDialog();
},500);
```







