# 教学文档  
## 1.引入文件  
```
<link rel="stylesheet" href="./css/table.css">
<link rel="stylesheet" href="./scroll_bar_fonts/iconfont.css">
<script src="./js/move.js"></script>
<script src="./js/table.js"></script>
```

## 2.html基础结构图
![图片名称](https://github.com/laoa1717/img-store/blob/master/%E5%9B%BE%E7%89%872.png?raw=true)  

**2.1  表格头部固定区域scroll-table-head**
```html
<!-- 表格头部固定区域 -->
<div class="scroll-table-head">
  <table class="tb1">
    <thead>
      <tr>
        <!-- <th style="width: 宽度自行定制(必填);">...</th> 例子如下-->
        <th style="width: 9em;">头部1</th>
        <th style="width: 8em;">头部2</th>
        <th style="width: 7em;">头部3</th>
        ............
      </tr>
    </thead>
  </table>
</div>
```  
