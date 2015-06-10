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
