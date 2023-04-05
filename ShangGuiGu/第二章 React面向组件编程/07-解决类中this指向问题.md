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

