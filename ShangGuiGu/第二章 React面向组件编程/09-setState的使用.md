# 之前例子的完善

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
                    this.changeWeather = this.changeWeather.bind(this)
            }
            render(){
                const {isHot} = this.state
                return <h2 onClick = {this.changeWeather}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }

            changeWeather(){
                // 获取原来isHot的值
                //因为此时的this以及指代的是Weather的实例化对象
                const isHot = this.state.isHot
                // 严重注意：状态（state）不可以直接更改，要借助内置的API去更改（setState）
                // 下面这行就是直接更改错误案例
                // this.state.isHot = !isHot

                //严重注意：状态必须通过setState进行修改（更新）
                this.setState ({isHot: !isHot}) //这种更新是一种合并而不是替换

            }
        }
        ReactDOM.render(<Weather/>, document.getElementById('test'))
    </script>
~~~

# 注意事项

1. 先获取state数据
2. **严重注意**：状态（state）的值不可以直接更改，要借助**内置的API进行修改（setState）**

​	错误案例如下：

~~~JavaScript
 const isHot = this.state.isHot
 this.state.isHot = !isHot
~~~

正确示范：

~~~JavaScript
this.setState ({isHot: !isHot})
~~~

3. setState只是进行了状态的合并并不是替换（如果之前还有一个状态，并没有对其进行修改，他还是会保留的）

# 思考问题

在这次变化中

### 构造器被调用了几次？

构造器只被调用一次，因为构造器只有被new一个实例的时候才会被调用，在这个代码中只有一个weather组件的实例（只有一个weather标签）

### render被调用了几次？

（1+n次），1是初始化的那次，n点的次数（状态更新的次数）

### changeWeather被调用了几次？

调用n次，点击此调几次