---
layout:     post
title:      "python中的时间操作"
date:       2015-06-24 22:56:00
author:     "jinlongwang"
header-img: "img/post-bg-05.jpg"
tag: "python"
---
###参考文章
  * [datetime<->timestamp](http://blog.jmoz.co.uk/python-convert-datetime-to-timestamp/)

    一.time模块  
  time模块提供各种操作时间的函数  
  一般有两种表示时间的方式:  
  第一种: 是时间戳的方式(相对于1970.1.1 00:00:00以秒计算的偏移量),时间戳是惟一的  
  第二种: 以数组的形式表示即(struct_time),共有九个元素，分别表示，同一个时间戳的struct_time会因为时区不同而不同  

  二.datetime模块  
  Python提供了多个内置模块用于操作日期时间，像calendar，time，datetime。time模块。  
  相比于time模块，datetime模块的接口则更直观、更容易调用。  
  datetime模块定义了下面这几个类：  
  datetime.date：表示日期的类。常用的属性有year, month, day；  
  datetime.time：表示时间的类。常用的属性有hour, minute, second, microsecond；  
  datetime.datetime：表示日期时间。  
  datetime.timedelta：表示时间间隔，即两个时间点之间的长度。  
  datetime.tzinfo：与时区有关的相关信息。  
  datetime中，表示日期时间的是一个datetime对象  
  datetime中提供了strftime方法，可以将一个datetime型日期转换成字符串：


<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = 'jinlongwang';

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
