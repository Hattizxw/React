# textarea

1. 他是一个self-closing的标签
2. 标签里的属性应该有：
   1. onChange函数
   2. name（和state对象中的名字一样）（目的：就是为了可以在onChange函数中找到被修改的是哪一个内容）
   3. value（对象名字.name值）（value其实是用来控制组件的）

# input

1. 也是一个self-closing标签
2. 标签属性
   1. type类型值（text和checkbox有很大区别）
   2. onChange函数
   3. name值
   4. value

# 代码

~~~jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: "", email: "", comments: ""}
    )
    
    console.log(formData.comments)
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    /**
     * Challenge: Add a textarea for "comments" to the form
     * Make sure to update state when it changes.
     */
    
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
            <textarea 
                value={formData.comments}
                placeholder="Comments"
                onChange={handleChange}
                name="comments"
            />
        </form>
    )
}
~~~

