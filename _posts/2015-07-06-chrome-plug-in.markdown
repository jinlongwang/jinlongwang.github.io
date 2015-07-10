---
layout:     post
title:      "写一个用来去掉知乎样式的chrome插件"
date:       2015-07-06 00:04:00
author:     "jinlongwang"
header-img: "img/post-bg-02.jpg"
tag: "chrome plugin"
---
最简单的chrome插件
======
###manifest.json
最主要的配置文件

        {
        "name": "clearZhihuCss",
        "version": "1.0",
        "description": "nobody can see what i'm look for",
        "permissions": [
        "tabs", "http://*/*", "https://*/*"
        ],
        "browser_action": {
          "default_title": "clear css",
          "default_icon": "icon.png",
          "default_popup": "popup.html"
        },
        "content_scripts": [
        {
          "matches": ["http://*/*", "https://*/*"],
          "js": ["jquery-1.11.2.js","content.js"]
        }
        ],
        "manifest_version": 2
        }

content_scripts中的脚本可以用于操作页面的dom
