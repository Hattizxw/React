# 代码

~~~jsx
import React from "react"

export default function Form() {
    
    const [formData, setFormData] = React.useState(
        {
            firstName: "",
            lastName: ""
        }
    )
    
    function handleChange (event){
       		 //我们是需要old State，因为一组对象中其他的值是不变的，我们需要保持其他的属性值不变，所以我们需要用callback function
            setFormData (prevFormData => {
                return {
                    ...prevFormData,
                    //这里的event.target.name，得到的值于formData中的对象匹配
                    //[event.target.name]记得加方括号
                    [event.target.name]: event.target.value
                }
            })
    }
    
    console.log(formData)
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                //这里的name属性值要和formData中的属性匹配
                name = "firstName"
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name = "lastName"
            />
        </form>
    )
}

~~~

# 注意

1. <input>标签中的name属性值很重要，要与formData中的对象名匹配
2. event.target.name获得formData中的对象名
3. event.target.value获得输入的值
4. [event.target.name]记得加方括号

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob24.PNG

# 学习网站

https://scrimba.com/learn/learnreact/forms-state-object-co4014fe8a23d6c6d376747ca



# 给input加value

value={formData.firstName}加上value之后，input中的值不是被input控制，而是被React。

每次运行handleChange函数的时候，更改formData中的数据，之后渲染到<input>标签中的value值

这样可以实现State来告诉input的值是什么（实现**状态控制**）

**如果不能很好的理解，但是也必须写上**

### 代码

~~~jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: "", email: ""}
    )
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
                value={formData.firstName}
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
                value={formData.lastName}
            />
            <input
                type="email"
                placeholder="Email"
                onChange={handleChange}
                name="email"
                value={formData.email}
            />
        </form>
    )
}
~~~

### 理解

受控组件的意思就是每当表单的状态发生变化时，都会被写入组件的state中，这种组件被称为受控组件

普通的组件无法改变输入框的值，那么将input组件和state结合起来再绑定onChange事件，最后再使用state实时更新value值，显示在input中，这样就形成了一个受控组件
