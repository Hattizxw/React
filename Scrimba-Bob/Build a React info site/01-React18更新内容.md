# 更新

之前版本都是将组件渲染到已经创建好的容器中，

~~~js
ReactDOM.render(<Navbar/>, document.getElementById("root"))
~~~

18版本之后的，我们可以将创建Root和渲染（render）放到一起

~~~js
ReactDOM.creatRoot(document.getElementById("root")).render(<Navbar/>)
~~~

or

~~~js
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<Navbar/>)
~~~

