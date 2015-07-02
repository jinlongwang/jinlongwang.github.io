---
layout:     post
title:      "'一键下班' or '水滴下拉刷新'？"
date:       2015-07-03 00:02:00
author:     "jinlongwang"
header-img: "img/post-bg-07.jpg"
tag: "canvas html5 贝塞尔曲线"
---
##参考文章
* [转载自AlloyTeam:使用web模拟手Q水滴下拉刷新效果](http://www.alloyteam.com/2015/06/shi-yong-web-mo-ni-shou-q-shui-di-xia-la-shua-xin-xiao-guo/)
* [手机 QQ 的一键消除红点功能是怎么想出来的？](http://www.zhihu.com/question/26382740)

##思路

####静态实现
  ![image](/img/qq.png)
  按照参考文章1中所述， 准备使用canvas实现。
  画两个圆加上两条贝塞尔曲线，来实现图中效果。
#####两个圆形

  canvas画圆形:

      context.arc(x,y,r,sAngle,eAngle,counterclockwise);


  1. x: 圆的中心的 x 坐标。
  2. y: 圆的中心的 y 坐标。
  3. r: 圆的半径。
  4. sAngle:起始角，以弧度计。（弧的圆形的三点钟位置是 0 度）。
  5. eAngle:结束角，以弧度计。
  * counterclockwise: 可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。

  ![image](/img/arc.png)

#####弧线

  画贝塞尔曲线：

      context.quadraticCurveTo(cpx,cpy,x,y);
  其实就三个主要要素：

  1.  开始点
  2.  控制点
  3.  结束点

#####坑

  遇到的最大的坑没想到居然是如何填充画完之后的图。
  最后的解决办法，一定要保证起始点和结束点重合，这样，
  closepath之后，在fill()就能出现我想要的！

#####代码和效果

    function draw(){
      var canvas=document.getElementById('canvas');
      var context=canvas.getContext('2d');
      context.fillStyle="#FF0000";
      context.strokeStyle = "red";
      //开始画图
      context.beginPath();

      //画第一条曲线
      context.moveTo(40,40);
      context.quadraticCurveTo(60,60,50,80);

      //底下的半圆
      context.arc(60,80,10, Math.PI, 0,true);

      //第二条曲线
      context.moveTo(70,80);
      context.quadraticCurveTo(60,60,80,40);
      //上圆
      context.arc(60,40,20, 0,Math.PI, true); //Math.PI*2是JS计算方法，是圆

      //填充
      context.closePath();
      context.stroke();
      context.fill();
    }

![image](/img/one.png)
![image](/img/two.png)

####Please 动起来！！
今天有点晚，明天再搞！！！













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
