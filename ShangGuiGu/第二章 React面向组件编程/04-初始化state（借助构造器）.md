# 通过一个小小的实例来实现

### 需求

网页内容会根据布尔值的不同输出的内容不同

### 分析

1. 给“炎热”加一个判断条件，如果isHot为真，则式“炎热”，如果为假，则为“寒冷”。这个isHot是要加入到state中去，然后我们读取state中isHot的值、我们要往state上放东西。
2. state是类（Weather）的实例对象上的，如果我们想要对类的实例对象进行初始化操作（增加属性，修改属性的值），**就需要构造器**
3. 也就是说，React中的React.Component类中有state这个属性，属性值是null，不符合我们想要的（无法满足我们的需求），所以我们要将state的值进行修改，**所以需要构造器**

# 类式组件的构造器

1. 普通类中的构造器中的参数是什么取决于**new的时候传入的参数。**
2. 但是在React中new这个操作是由渲染的时候**系统自动给new 的**
3. 所以在React中，**构造器接受的参数是props**
4. super（）也是必须有的

~~~JavaScript
constructor(props){
                    super(props)
    				//初始化状态
                    this.state = {isHot: true }
    //在组件身上修改数据
}
~~~

# **已经将表达天气炎热的数据维护到了state中**

# **下一步就是读取state，并做判断**

~~~JavaScript
render(){
                return <h2>今天天气很{this.state.isHot ? '炎热' : '寒冷'}</h2>
    //读取数据
            }
~~~

~~~JavaScript
render(){
                const {isHot} = this.state
                return <h2>今天天气很{isHot ? '炎热' : '寒冷' }</h2>
            }
~~~

因为this就是实例化对象



# 完整代码

~~~JavaScript
<script type="text/babel">
        class Weather extends React.Component{
            constructor(props){
                    super(props)
                //初始化状态
                    this.state = {isHot: true }
            }
            render(){
                //读取状态
                return <h2>今天天气很{this.state.isHot ? '炎热' : '寒冷'}</h2>
            }
        }

        ReactDOM.render(<Weather/>, document.getElementById('test'))
</script>
~~~

# 效果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React06.PNG