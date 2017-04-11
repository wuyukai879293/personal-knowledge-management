# 第7章 Spring MVC 高级性能
在本章中我们将谈论一些5、6章之外的一些特性。我们将学到如何写一个文件上传的控制器，如何处理控制器异常，~~以及如何在Model中传输数据~~。在这之前，我们先来了解一下启动Spring MVC 的几种方法，前面章节我们介绍过通过`AbstractAnnotationConfigDispatcherServletInitializer`的方式启动，现在我们来介绍一些其他的方式来启动`DispatcherServlet`和`ContextLoaderListener`。  

## 7.1 替换 Spring MVC 配置
第5章中通过`AbstractAnnotationConfigDispatcherServletInitializer`的方式可以配置基本的`DispatcherServlet`和`ContextLoaderListener`，但是这样的方式并不总是满足我们的要求。例如：当你除`DispatcherServlet`之外还需要 servlets 和 filters ，或是需要对`DispatcherServlet`作一些额外的配置，或者部署在一个 servlet 3.0之前的容器上，需要通过传统的web.xml的方式来配置。这些不足使得我们需要定制`DispatcherServlet`.
### 7.1.1 定制 DispatcherServlet 配置
在 5.1 的程序清单中我们只重写了`AbstractAnnotationConfigDispatcherServletInitializer`中的三个抽象方法，但是其中还有更多的方法可以重写，比如`customizeRegistration()`。使用这个方法，我们可以对servlet的注册进行更多的个性化操作（因为 Inintializer 对 DispatcherServlet 注册后即会调用该方法）。
### 7.1.2 添加额外的控制器和过滤器
`AbstractAnnotationConfigDispatcherServletInitializer`只能生成`DispatcherServlet`和`ContextLoaderListener`。通过创建一个`WebApplicationInitializer`接口的实例，来注册控制器，过滤器和监听器。如果只需要几个过滤器并将它们映射到`DispatcherServlet`,只需简单的重写默认初始化器的`getServletFilters()`方法即可。
### 7.1.3 在 web.xml 中声明 DispatcherServlet
如果在web.xml文件中注册`DispatcherServlet`和`ContextLoaderListener`，需要手动做所有的设置。`DispatcherServlet`和`ContextLoaderListener`分别加载一个Spring 应用上下文。每个都包含参数来设置其加载Bean的位置。
