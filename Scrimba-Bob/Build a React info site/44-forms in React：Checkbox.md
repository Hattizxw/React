# checkbox

checkbox是input标签中的一种类型，

标签属性

1. type = “checkbox”
2. name
3. id （要和label进行绑定，我们会在label标签中设置htmlFor属性，这个属性值和id的值一样，**表示将label标签绑定到了这个checkbox表单元素上**）
4. onChange函数
5. checked（**由于checkbox没有value，所以这个属性的作用和value的作用一样**）（为了实现组件控制）

# 代码

~~~jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {
            firstName: "", 
            lastName: "", 
            email: "", 
            comments: "", 
            isFriendly: true   //注意复选框的初始值应该是布尔值
        }
    )
    
    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                //这里有一个三元判断符，表示查看type的类型是什么，如果是checkbox，name后面跟着的就应该是checked
                [name]: type === "checkbox" ? checked : value
            }
        })
    }
    
    //htmlFor 属性设置或返回 label 的 for 属性的值。

    // for 属性指定 label 要绑定到哪一个表单元素。
    
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
            <input 
                type="checkbox" 
                name="isFriendly"
                checked={formData.isFriendly}   //只有选和不选（false和true）两个值
                onChange={handleChange}
                id="isFriendly" 
            />
            <label htmlFor="isFriendly">Are you friendly?</label>
            <br />
        </form>
    )
}
~~~

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob25.PNG

