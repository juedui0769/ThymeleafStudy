> thymeleafexamples-gtvg

这是从官网拷贝的样例
- <https://github.com/thymeleaf/thymeleafexamples-gtvg>
- 对应的在线文档是 : <https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html> ,
- 可以在 <https://www.thymeleaf.org/documentation.html> 下载PDF版本.
- 这是我阅读'usingthymeleaf.pdf'时做得笔记: <https://github.com/juedui0769/BitCode2018/blob/master/Thymeleaf-Study/README.md>

src/webapp/WEB-INF/templates
- 此目录下的模板文件是最好的学习`Thymeleaf`的参照

```xml
<filter>
    <filter-name>gtvgfilter</filter-name>
    <filter-class>thymeleafexamples.gtvg.web.filter.GTVGFilter</filter-class>
</filter>
```

如上, `web.xml`中配置的是`GTVGFilter`类,这个filter就是整个项目的入口了。
- `GTVGFilter` 是一个很好的 filter 使用样例
- `GTVGApplication` 扮演了很重要的角色
- `IGTVGController` 是所有控制类需要继承的接口
- 路由信息都放在 `GTVGApplication` 类的成员属性 `controllersByURL:Map<String, IGTVGController>` (map) 中, 在`GTVGApplication`构造方法中初始化。
- 没有数据库, 所有数据都是直接定义在类中的。

```java
ServletContextTemplateResolver templateResolver = new ServletContextTemplateResolver(servletContext);

// HTML is the default mode, but we will set it anyway for better understanding of code
templateResolver.setTemplateMode(TemplateMode.HTML);
// This will convert "home" to "/WEB-INF/templates/home.html"
templateResolver.setPrefix("/WEB-INF/templates/");
templateResolver.setSuffix(".html");
// Set template cache TTL to 1 hour. If not set, entries would live in cache until expelled by LRU
templateResolver.setCacheTTLMs(Long.valueOf(3600000L));

// Cache is set to true by default. Set to false if you want templates to
// be automatically updated when modified.
templateResolver.setCacheable(true);

this.templateEngine = new TemplateEngine();
this.templateEngine.setTemplateResolver(templateResolver);
```

上面这段代码来自`GTVGApplication`的构造方法, 这段代码展示了以编程方式设置和启用`Thymeleaf`的步骤。





