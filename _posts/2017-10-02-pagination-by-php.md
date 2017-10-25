---
layout:         post
title:          php实现分页
subtitle:       pagination by php
card-image:     https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1508909709290&di=84ae3e65c50c06b8aba003aac9098c2c&imgtype=0&src=http%3A%2F%2Fwww.sucaihuo.com%2Fjquery%2F11%2F1175%2Fbig.jpg
date:           2017-10-02 8:04:15
tags:           code
post-card-type: image
---

```html
    <!DOCTYPE html>    
    <html xmlns="http://www.w3.org/1999/xhtml">    
    <head>    
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />    
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no" />    
    <link href="http://apps.bdimg.com/libs/bootstrap/3.3.0/css/bootstrap.min.css" rel="stylesheet">    
    <script src="http://apps.bdimg.com/libs/jquery/2.0.0/jquery.min.js"></script>    
    <script src="http://apps.bdimg.com/libs/bootstrap/3.3.0/js/bootstrap.min.js"></script>    
    </head>       
    <body>    
    <div class="panel panel-default">    
        <div class="panel-body">    
            <table class="table table-hover">    
                <thead>    
                    <tr>    
                        <th>a</th>    
                        <th>b</th>    
                        <th>c</th>    
                        <th>d</th>    
                        <th>e</th>    
                        <th>f</th>    
                    </tr>    
                </thead>    
                <?php if($num>0){?>    
                <tbody>    
                <?php  while($row=mysql_fetch_array ( $res ) ){?>    
                    <tr>    
                        <td><?php echo $row['a'];?></td>    
                        <td><?php echo $row['b'];?></td>    
                        <td><?php echo $row['c'];?></td>    
                        <td><?php echo $row['d'];?></td>    
                        <td><?php echo $row['e'];?></td>    
                        <td><?php echo $row['f'];?></td>    
                        <!--<td><?php if($row['dingdan_status']==1){?><span class="label label-success">已付</span><?php }else{?><span class="label label-warning">未付</span><?php }?></td>-->    
                    </tr>    
                <?php }?>    
                <?php }else{?>    
                <tr><td colspan="6" class="text-center">暂无记录</td></tr>    
                <?php }?>    
                </tbody>    
            </table>    
            <ul class="pagination">    
            <?php    
            if ($page != 1) { //页数不等于1    
            ?>    
                <li><a href="List.php?page=<?php echo $page - 1;?>">?</a></li>    
            <?php    
            }    
            for ($i=1;$i<=$totalPage;$i++) {  //循环显示出页面    
            ?>    
                <li><a href="List.php?page=<?php echo $i;?>"><?php echo $i ;?></a></li>    
            <?php    
            }    
            if ($page<$totalPage) { //如果page小于总页数,显示下一页链接    
            ?>    
                <li><a href="List.php?page=<?php echo $page + 1;?>">?</a></li>    
            <?php    
            }     
            mysql_close( $link );    
            ?>    
            </ul>    
        </div>    
    </div>    
    </body>    
    </html>  
	
	
	
```php    
<?php    
    ///////////    
    //数据库连接    
    ///////////    
    //假设取出list表中所有数据    
    $perNumber = 15; // 每页显示的记录数    
    $page = $_GET ['page']; // 获得当前的页面值    
    $count = mysql_query ( "select count(*) from `list` "); // 获得记录总数    
        
    $rs = mysql_fetch_array ( $count );    
    $totalNumber = $rs [0];    
    $totalPage = ceil ( $totalNumber / $perNumber ); // 计算出总页数    
    if (! isset ( $page )) {    
        $page = 1;    
    } // 如果没有值,则赋值1    
    $startCount = ($page - 1) * $perNumber; // 分页开始,根据此方法计算出开始的记录    
        
    // 根据前面的计算出开始的记录和记录数    
    $sqq="select * from `list` limit $startCount,$perNumber";    
    $res=mysql_query($sqq);    
    $num=mysql_num_rows($res);    
        
?> 
```