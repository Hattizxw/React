# 需求

1. 对传递进去的标签属性进行类型限制
2. 进行必要性的限制
3. 给某个属性指定默认值

# 分析

也就是对组件实例对象中的props进行限制（传递的东西进行限制）

# 引入prop-types.js文件

用于对组件标签属性进行限制

# 进行必要性和类型限制

~~~JavaScript
Person.propTypes = {   //代表Person中的props规则
            name: PropTypes.string.isRequired,   //限制name必传并且为字符串类型
            sex: PropTypes.string,   //限制sex为字符串类型
            age:PropTypes.number,    //限制age为数字类型
            speak: PropTypes.func,   //限制speak为函数类型
        }
~~~

### 特别注意

这里的字符串和数组都是**首字母小写，**

为了避免和系统**内置对象冲突，**

但是function是定义函数的关键字，所以不能直接写function，要写为func

# 指定默认标签属性值

~~~JavaScript
 Person.defaultProps = {
            sex: '不男不女',
            age: 18
        }
~~~

# 完整代码

~~~JavaScript
<body>
     <!-- 准备一个容器 -->
     <div id="test1"></div>
     <div id="test2"></div>

     <!-- 引入依赖 -->
     <script type="text/javascript" src="./js/react.development.js"></script>
     <script type="text/javascript" src="./js/react-dom.development.js"></script>
     <script type="text/javascript" src="./js/babel.min.js"></script>
     <script type="text/javascript" src="./js/prop-types.js"></script>

     <script type="text/babel">
        //创建组件
        class Person extends React.Component{
            render (){
                const {name, age, sex } = this.props
                return (
                    <ul>
                        <li>姓名：{name}</li>
                        <li>年龄：{age}</li>    
                        <li>性别：{sex}</li>  
                    </ul>
                )
            }
        }

        //进行props的限制
        //给Person中的props进行限定
        //进行必要性和类型限制
        Person.propTypes = {   //代表Person中的props规则
            name: PropTypes.string.isRequired,   //限制name必传并且为字符串类型
            sex: PropTypes.string,   //限制sex为字符串类型
            age:PropTypes.number,    //限制age为数字类型
            speak: PropTypes.func,   //限制speak为函数类型
        }
        // 指定默认标签属性值
        Person.defaultProps = {
            sex: '不男不女',
            age: 18
        }

        // 渲染
        ReactDOM.render(<Person name = "CouYee" age = "18" sex = "女" speak = {speak}/>, document.getElementById('test1'))
        ReactDOM.render(<Person name = "jackson" age = "18" sex = "男"/>, document.getElementById('test2'))

        function speak(){
            console.log('我说话了');
        }
     </script>
</body>
~~~

