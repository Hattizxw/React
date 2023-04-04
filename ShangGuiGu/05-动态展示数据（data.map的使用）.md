# 需求

动态的把数组中的数据以li标签的形式展示出来

# 效果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React04.PNG

# 代码以及讲解

~~~JavaScript
	<!-- 准备一个容器 -->
    <div id="test"></div>
    <!-- 引入react依赖 -->
    <script type="text/javascript" src="./js/react.development.js"></script>
    <script type="text/javascript" src="./js/react-dom.development.js"></script>
    <script type="text/javascript" src="./js/babel.min.js"></script>

    <script type="text/babel">
        //模拟数据
        const data = ['Angular','React','Vue']
        //创建一个虚拟DOM
        const VDOM = (
            // <div>
            //     <h1>前端js框架列表</h1> 
                   
            //     <ul>
            //         <li>Angular</li>
            //         <li>React</li>
            //         <li>Vue</li>
            //     </ul>
            // </div>
            

            //动态数据
            //将字符串加工成带有标签的数据
            <div>
                <h1>前端js框架列表</h1>    
                <ul>
                    {
                        //item表示拿到的每一个数据
                        //每一个结点都要都一个唯一的key属性，就是说，页面中有许多的li，但是每一个li都是不同的，所以我们要给							每一个li加一个唯一的key属性
                        data.map((item,index)=>{
                            return <li key = {index}>{item}</li>
                        })

                        //index这样作为key不合理，后面会用别的方法，
                        //我们只需要知道便利的时候，列表中每一个元素都得有一个唯一值key
                    }
                </ul>
            </div>
        )

        //渲染
        ReactDOM.render(VDOM, document.getElementById('test'))
    </script>
~~~

