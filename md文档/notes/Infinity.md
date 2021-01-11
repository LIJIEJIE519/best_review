# Infinity

## FullCalendar：日程表

https://blog.csdn.net/kylinregister/article/details/82988517

https://www.helloweba.net/javascript/445.html

### 1. 引入中文支持

![image-20201112232945184](/Users/star/Library/Application Support/typora-user-images/image-20201112232945184.png)



### 2. 使用简介

https://blog.csdn.net/bk_show/article/details/80352833



## moment：时间格式化器

http://momentjs.cn/

### 1. 引入中文支持

![image-20201112233311534](/Users/star/Library/Application Support/typora-user-images/image-20201112233311534.png)



### 2. 





## DataTables：表格插件

http://datatables.club/

https://blog.csdn.net/zixuan701/article/details/89189121

### 1. 引入中文支持

https://www.cnblogs.com/xwgli/p/9265182.html

![image-20201112234043933](/Users/star/Library/Application Support/typora-user-images/image-20201112234043933.png)

```javascript
$.fn.dataTable.defaults.oLanguage = {
    "sProcessing": "处理中...",
    "sLengthMenu": "显示 _MENU_ 项结果",
    "sZeroRecords": "没有匹配结果",
    "sInfo": "显示第 _START_ 至 _END_ 项结果，共 _TOTAL_ 项",
    "sInfoEmpty": "显示第 0 至 0 项结果，共 0 项",
    "sInfoFiltered": "(由 _MAX_ 项结果过滤)",
    "sInfoPostFix": "",
    "sSearch": "搜索：",
    "sUrl": "",
    "sEmptyTable": "表中数据为空",
    "sLoadingRecords": "载入中...",
    "sInfoThousands": ",",
    "oPaginate": {
        "sFirst": "首页",
        "sPrevious": "上页",
        "sNext": "下页",
        "sLast": "末页"
    },
    "oAria": {
        "sSortAscending": ": 以升序排列此列",
        "sSortDescending": ": 以降序排列此列"
    }
};

// datatable 默认配置
$.extend( $.fn.dataTable.defaults, {
    "searching": false, //去掉搜索框方法一
    "bLengthChange": false,
    // "bSort": false,  //禁止排序
    // "paging": false,   //禁止分页
    // "info": false   //去掉底部文字
});
```

