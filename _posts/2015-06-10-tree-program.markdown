---
layout:     post
title:      "关于二叉树的算法题目"
date:       2015-06-10 22:55:00
author:     "jinlongwang"
header-img: "img/post-bg-02.jpg"
tag: "算法"
---
####python的二叉树结构
    class Tree(object):
      def __init__(self, data=None, left=None, right=None):
          self.data = data
          self.left = left
          self.right = right

####构造一棵二叉树
![image](/img/btree.png)

####3种遍历方式
    def preTraverse(root):
      if root == None:
          return
      print root.data
      preTraverse(root.left)
      preTraverse(root.right)

    def middleTraverse(root):
      if root == None:
          return
      middleTraverse(root.left)
      print root.data
      middleTraverse(root.right)

    def afterTraverse(root):
      if root == None:
          return
      afterTraverse(root.left)
      afterTraverse(root.right)
      print root.data

    if __name__ == "__main__":
      root = Tree("A",Tree("B", Tree("D"),Tree("E")), Tree("C", Tree("F"), Tree("G")))
      print '-------pre--------'
      preTraverse(root)
      print '-------middle-----'
      middleTraverse(root)
      print '-------end--------'
      afterTraverse(root)


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
