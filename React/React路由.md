<a name="SoQVP"></a>
## 相关理解
<a name="IlQwp"></a>
### SPA的理解

1. 单页面Web应用（single page web application，SPA）
2. 整个应用只有一个完整的页面
3. 点击页面中的连接不会刷新页面，只会做页面的局部更新。
4. 数据都需要通过ajax请求获取，并在前端异步展现。
<a name="TCuAB"></a>
### 路由的理解
<a name="n5idk"></a>
#### 什么是路由？

1. 一个路由就是一个映射关系（key.value）
2. key为路径path，value可能是function或component
<a name="r2X0J"></a>
#### 路由分类

1. 后端路由：
   1. 理解：value是function，用来处理客户端提交的请求
   2. 注册路径：router.get(path,function(req,res))
   3. 工作过程：当node接收到一个请求时，根据请求路径找到匹配的路由， 调用路由中的函数来处理请求，返回响应数据。
2. 前端路由：
   1. 浏览器端路由，value是component，组件，用于展示页面内容
   2. 注册路由：<Route path="/test" component={Test} />  <Route path="/test" element={<Test />} />
   3. 工作过程：当浏览器的path变为/test时，当前路由组件就会变为Test组件。
3. 前端路由靠浏览器history BOM是浏览器对象，有history。借助history.js库来监测。
   1. history.listen 
   2. 浏览器的历史记录是一个栈的结构，先进后出为栈，先进先出为队列有push和replace方法 
   3. 方法1:let history = History.createBrowserHistory() 直接用H5退出的history身上的API
   4. 方法2:let history = History.creatHashHistory() 直接使用H5退出的history身上的API
<a name="op3R3"></a>
#### react-router-dom的理解

1. react的一个插件库。
2. 专门用来实现一个SPA应用
3. 基于react的项目基本都会用到此库。
<a name="NsFN8"></a>
## react-router-dom相关API
<a name="MSsd8"></a>
### 内置组件

1. <BrowserRotuer>
2. <HashRouter>
3. <Route>
4. <Redirect>
5. <Link>
6. <NavLink>
7. <Switch>

