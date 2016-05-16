---

layout:     post
title:      "django class based view 代码分析"
date:       2016-04-09 00:01:00
author:     "jinlongwang"
header-img: "img/post-bg-01.jpg"

---

# django class based view 代码分析

1. url.py入手

	`class view` url配置一般这样写
			
			url(r'^module_detail/(?P<pk>(\d+))/$' ModuleDetailView.as_view(), name='module_detail'),
			
	关键方法是`as_view()`。

2. `as_view()` 源码
	 	`as_view()`方法实际是个闭包， 返回了一个处理函数， 把class view 变成了function view， 源码如下：
 		
 		def as_view(cls, **initkwargs):
        """
        Main entry point for a request-response process.
        """
        for key in initkwargs:
            if key in cls.http_method_names:
                raise TypeError("You tried to pass in the %s method name as a "
                                "keyword argument to %s(). Don't do that."
                                % (key, cls.__name__))
            if not hasattr(cls, key):
                raise TypeError("%s() received an invalid keyword %r. as_view "
                                "only accepts arguments that are already "
                                "attributes of the class." % (cls.__name__, key))

        def view(request, *args, **kwargs):
            self = cls(**initkwargs)
            if hasattr(self, 'get') and not hasattr(self, 'head'):
                self.head = self.get
            self.request = request
            self.args = args
            self.kwargs = kwargs
            return self.dispatch(request, *args, **kwargs)
        view.view_class = cls
        view.view_initkwargs = initkwargs

        # take name and docstring from class
        update_wrapper(view, cls, updated=())

        # and possible attributes set by decorators
        # like csrf_exempt from dispatch
        update_wrapper(view, cls.dispatch, assigned=())
        return view
        
还可以看到， 方法中实际调用了`self.dispatch(request, *args, **kwargs)`

3. `self.dispatch`做了什么？
    直接看`dispatch`代码
    
    	def dispatch(self, request, *args, **kwargs):
        # Try to dispatch to the right method; if a method doesn't exist,
        # defer to the error handler. Also defer to the error handler if the
        # request method isn't on the approved list.
        if request.method.lower() in self.http_method_names:
            handler = getattr(self, request.method.lower(), self.http_method_not_allowed)
        else:
            handler = self.http_method_not_allowed
        return handler(request, *args, **kwargs)
      
    通过`getattr`方法动态调用对应的method， 如`get`, `post`等
    
4. 看一个DetailView的实现方式
   
   * 类图
   
   ![image](/img/django_class_view.png)
    

