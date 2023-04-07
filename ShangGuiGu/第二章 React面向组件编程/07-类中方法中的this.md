# 错误的调用

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
            }
            render(){
                const {isHot} = this.state
                //这样子就是直接函数调用，通过类的实例对象，沿着原型链查找找到了changeWeather，然后直接将函数交给onClick直接作为回调。当我们点击h2时，直接将函数从堆里面拉出来执行，并不是通过实例进行调用
                return <h2 onClick = {this.changeWeather}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }

            changeWeather(){
                //changeWeather放在那里？ ---- Weather的原型对象上，供实例使用
                //由于changeWeather是作为onClick的回调，所以不是通过实例调用的，是直接调用的
                //类中的方法默认开启了局部的严格模式，所以changeWeather中的this为undefined
                console.log(this);
            }
        }

        ReactDOM.render(<Weather/>, document.getElementById('test'))
    </script>
~~~

1. render被调用是通过渲染时，实例调用原型上的render方法，所以，render中的this指向的就是实例
2. 如果按照错的onClick中的写法。这样子就是**直接函数调用**，通过类的实例对象，沿着原型链查找找到了changeWeather，然后直接将函数交给onClick直接作为回调。当我们点击h2时，直接将函数从堆里面拉出来执行，并不是通过实例进行调用。
3. 类中的方法默认开启了局部的严格模式，所以changeWeather中的this为undefined