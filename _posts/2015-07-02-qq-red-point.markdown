---
layout:     post
title:      "'一键下班' or '水滴下拉刷新'？"
date:       2015-06-24 22:56:00
author:     "jinlongwang"
header-img: "img/post-bg-07.jpg"
tag: "canvas html5 贝塞尔曲线"
---
###参考文章
* [转载自AlloyTeam:使用web模拟手Q水滴下拉刷新效果](http://www.alloyteam.com/2015/06/shi-yong-web-mo-ni-shou-q-shui-di-xia-la-shua-xin-xiao-guo/)
* [手机 QQ 的一键消除红点功能是怎么想出来的？](http://www.zhihu.com/question/26382740)

###思路
#####静态实现
  ![image](/img/qq.png)
  按照参考文章1中所述， 准备使用canvas实现。
  画两个圆加上两条贝塞尔曲线，来实现图中效果。
  


####代码

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
