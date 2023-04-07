# 作用

从组件外部给组件内部带数据进去

# 注意

props只读

# 使用

1. 由于，render中的this是组件实例对象，其身上有一个**属性是props**
2. HTML标签可以写标签属性，标签属性就是key和value的组合
3. 所以组件标签也可以这样写，这时，我们就可以传入各种属性和属性值给render

（当我们渲染<Person name="Tom"/>时，React在new这个person实例的时候，会自动的把name作为key，Tom作为value，放到props中）

4. render在返回值中可以直接使用

# 例子

~~~JavaScript
<script type="text/babel">
        //创建组件
        class Person extends React.Component{
            render (){
                return (
                    <ul>
                        <li>姓名：{this.props.name}</li>
                        <li>年龄：{this.props.age}</li>    
                    </ul>
                )
            }
        }
        // 渲染
        ReactDOM.render(<Person name = "CouYee" age = "18"/>, document.getElementById('test'))
</script>
~~~

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React07.PNG

# 结构赋值写法

~~~JavaScript
<script type="text/babel">
        //创建组件
        class Person extends React.Component{
            render (){
                // 结构赋值写法
                const {name, age} = this.props
                return (
                    <ul>
                        <li>姓名：{name}</li>
                        <li>年龄：{age}</li>    
                    </ul>
                )
            }
        }
        // 渲染
        ReactDOM.render(<Person name = "CouYee" age = "18"/>, document.getElementById('test'))
     </script>
~~~

