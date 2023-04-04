# 关于虚拟DOM

1. 本质是一个Object类型的对象
2. 虚拟DOM比较“轻”（身上的属性少），真实DOM比较“重”，因为虚拟DOM是React内部在用，无需真实DOM上那么多的属性
3. 虚拟DOM最终会被React会被React转换成真实DOM。呈现在页面上。

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

        const TDOM = document.getElementById('test')
        console.log('真实DOM', TDOM);
        console.log('虚拟DOM', VDOM);
    </script>
~~~

### 代码运行结果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React03.PNG