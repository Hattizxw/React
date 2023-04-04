# React安装

- react包是核心，提供创建元素、组件等功能
- react-dom 包提供dom相关功能等 （将创建好的元素渲染到页面中）

# 运行命令（创建react项目）

- npm install create-react-app --(locally)
- npx create-react-app newapp
- 进入newapp文件夹
- npm start

# 或者简单引入网页版的js文件

~~~JavaScript
<script src="https://cdn.bootcss.com/react/16.4.0/umd/react.development.js"></script>
<script src="https://cdn.bootcss.com/react-dom/16.4.0/umd/react-dom.development.js"></script>
<script src="https://cdn.bootcss.com/babel-standalone/6.26.0/babel.min.js"></script>
~~~

# 或者直接引入js文件

~~~JavaScript
<script type="text/javascript" src="./js/react.development.js"></script>
<script type="text/javascript" src="./js/react-dom.development.js"></script>
<script type="text/javascript" src="./js/babel.min.js"></script>
~~~

# 简单案例

~~~JavaScript
	<!-- 准备一个容器 -->
	<div id="test"></div>

	<!-- 引入react依赖 -->
    <!-- 
    <script src="https://cdn.bootcss.com/react/16.4.0/umd/react.development.js"></script>
    <script src="https://cdn.bootcss.com/react-dom/16.4.0/umd/react-dom.development.js"></script>
    <script src="https://cdn.bootcss.com/babel-standalone/6.26.0/babel.min.js"></script> 
    -->
    <script type="text/javascript" src="./js/react.development.js"></script>
    <script type="text/javascript" src="./js/react-dom.development.js"></script>
    <script type="text/javascript" src="./js/babel.min.js"></script>

    <!-- 此处一定要写babel要不系统默认你写的是js，实际你写的是jsx -->
    <script type="text/babel">   
        // 创建虚拟DOM
        const VDOM = <h1>Hello,React</h1>   //此处一定不要写单引号
        // 渲染虚拟DOM到页面
        // ReactDOM.render(虚拟DOM，容器)
        ReactDOM.render(VDOM, document.getElementById('test'))  //react没有提供选择器
    </script>
~~~

babel将你写的jsx文件转换成js

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React02.PNG