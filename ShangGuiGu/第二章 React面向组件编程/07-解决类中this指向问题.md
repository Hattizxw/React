# 解决方法

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
                    //等号右边：
                    //this是组件的实例对象
                    //由于changeWeather放在了Weather的原型对象上，纵使实例自身没有，也会顺着原型链找到原型上
                    //所以，this.changeWeather找到的是Weather类中的changeWeather方法
                    //bind的作用，第一个是帮忙生成新的函数，第二个是帮忙改变函数中的this，
                    //由于这里传入的this指的是，实例对象
                    //所以右边的代码指代的是，表示一个新的函数，并且函数中的this指代的是weather的实例对象。并且把它放到了实例自身
                    this.changeWeather = this.changeWeather.bind(this)
            }
            render(){
                const {isHot} = this.state
                //这里面调用的changeWeather表示的是挂在自身上的，而不是原型上的
                return <h2 onClick = {this.changeWeather}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }

            //原型上的
            changeWeather(){
                console.log(this);  
            }
        }

</script>
~~~

# 重点讲解

~~~JavaScript
this.changeWeather = this.changeWeather.bind(this)   //实例自身  ===  原型上的
~~~

等号右边：

this表示的是组件的实例对象

由于changeWeather放在了Weather的原型对象上，纵使实例自身没有，也会顺着原型链找到原型上

所以，this.changeWeather找到的是Weather类中的changeWeather方法

bind的作用，第一个是帮忙生成新的函数，第二个是帮忙改变函数中的this，

由于这里传入的this指的是，实例对象

**所以右边的代码指代的是，表示一个新的函数，并且函数中的this指代的是weather的实例对象。并且把它放到了实例自身**

~~~JavaScript
 return <h2 onClick = {this.changeWeather}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>   //实例自身
~~~

这里面调用的changeWeather表示的是挂在自身上的，而不是原型上的

# 对应关系

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
                    this.demo = this.changeWeather.bind(this)
            }
            render(){
                const {isHot} = this.state
                return <h2 onClick = {this.demo}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }

            changeWeather(){
                console.log(this);
            }
        }

        ReactDOM.render(<Weather/>, document.getElementById('test'))
</script>
~~~

~~~JavaScript
 <script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
                    this.nice = this.test.bind(this)
            }
            render(){
                const {isHot} = this.state
                return <h2 onClick = {this.nice}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }

            test(){
                console.log(this);
            }
        }

        ReactDOM.render(<Weather/>, document.getElementById('test'))
</script>
~~~

# 三部分的this具体理解

### 构造器

构造器中的this就是该类的实例对象

### render

render中的this也是实例对象

##### 原因

主要是因为渲染的时候，我们写了<Weather/>标签

在react系统中，系统自动给我们new 了一个Weather

~~~JavaScript
 const w1 = new Weather()
~~~

然后系统通过w1.render完成了调用，

所有这里的this也没问题

### changeWeather（自定义方法都是作为回调进行使用）

这里面的this**并不是w1进行的调用**，

而是作为事件的**回调**在进行使用

当我们触发了点击事件之后，我们直接把函数拉出来**直接调用**，并不是通过实例进行调用，

所以这里的this指向的是window，但是由于类有严格控制模式，所以this是undefined
