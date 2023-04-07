# 方法

1. 我们想给所有的Weather对象都追加一个state属性，所以，我们可以把**state直接放到类里面**
2. 自定义的函数变为**赋值语句＋箭头函数**
   1. 因为箭头函数没有自己的this，但是如果在箭头函数中使用了this，它会自动找其外层函数的this，作为箭头函数的this使用（在这里就是weather的实例对象）
   2. 关于赋值语句，和state原理一样，直接写赋值，代表每一个实例对象都有了changeWeather这个属性

3. **删除构造器**

~~~JavaScript
<script type="text/babel">
        //创建组件
        class Weather extends React.Component {
            // constructor(props){
            //     super(props)
            //     this.state = {isHot: false}
            //     this.changeWeather = this.changeWeather.bind(this)
            // }
            //在weather的实例对象身上都添加一个属性，名为state，值为一个对象
            //初始化状态
            state = {isHot: false}
            render(){
                const isHot = this.state.isHot
                return <h2 onClick = {this.changeWeather}>今天天气很{isHot ? '炎热':'寒冷'}</h2>
            }
            //自定义方法
            changeWeather = () => {
                const isHot = this.state.isHot
                this.setState ({isHot: !isHot})
            }
        }
        // 渲染
        ReactDOM.render(<Weather/>, document.getElementById('test'))
    </script>
~~~



# 自我理解

1. 在写代码的时候**render中肯定要写this**的，因为render就是为了读取数据，**数据都是实例对象中**的
2. 同样自定义函数也是这个道理