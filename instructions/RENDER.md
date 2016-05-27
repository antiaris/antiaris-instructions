# 渲染篇

在 2016 年，HTML 的渲染模式已经非常丰富，但仍可划分为两类：前端渲染和后端渲染。在以 MVVM 框架为代表的前端渲染框架中，著名的有 Angular、vue、Ember 等。这类框架用户与服务之间进行数据（或者是 RESTFUL API）解耦，服务端渲染逻辑可以相当简单：只输出了页面框架即可。这样的设计将直接面临一个问题：速度/性能，特别是在移动环境中，白屏时间是绝对难以接受的。

后端渲染以模板引擎为代表，冉生出 React/Angular2 等后端渲染方案，这里只考虑后端渲染。

无论哪种方案，架构上都应该和框架解耦开来。比如 App1 使用模板引擎， App2 使用 React，甚至同一个应用不同的路由都允许不同，因为后端渲染的本质无非就是拼接字符串而已。

如
```js
router.get('/index', function() {
    return '<html></html>'
});

router.get('/user', function() {
    return this.render('user.tpl');
});

router.get('/profile', function() {
    return ReactDOMServer.renderToString(<Profile/>);
});
```


