# 代码

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                    this.state = {isHot: false }
            }
            render(){
                //this也是实例对象
                const {isHot} = this.state
                return <h2 onClick = {demo}>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }
        }

        ReactDOM.render(<Weather/>, document.getElementById('test'))

        function demo(){
            console.log('标题被点击了');
        }
</script>
~~~

# 注意

1. React中的绑定事件都用嵌套在标签中的这种形式，并且名字和原生js有些许不用（**命名用小驼峰**）
2. React中要求将onClick = ....函数调用的返回值传递给 onClick，但是函数是一个函数调用表达式，demo的返回值是一个undefined，
3. 所以，如果给demo加上（）导致了函数调用。当我们执行点击函数的时候，帮我们调用undefined
4. 所以我们**只需要写函数名**，  表示，

~~~JavaScript
 onClick = {demo}
~~~

**是一个赋值语句，我们要将右边的函数交给onClick作为回调，你点击的时候，系统给调用demo**