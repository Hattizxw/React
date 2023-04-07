# 语法

批量展开某一个实例的数据

~~~JavaScript
<script type="text/babel">
        //创建组件
        class Person extends React.Component{
            render (){
                const {name, age,sex} = this.props
                return (
                    <ul>
                        <li>姓名：{name}</li>
                        <li>年龄：{age}</li>    
                        <li>性别：{sex}</li> 
                    </ul>
                )
            }
        }
        // 渲染
        const p ={name: 'CouYee', age: 18, sex: '女'}
        ReactDOM.render(<Person {...p}/>, document.getElementById('test'))
     </script>
~~~

在这里虽然展开运算符不能便利对象，但是在这里，由于babel和React的新语法，仅仅适用于标签属性的传递

**可以用展开运算符去展开一个对象**，而不是复制对象

