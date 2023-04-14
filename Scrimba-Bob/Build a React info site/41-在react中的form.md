# 获取表单中（input）中的值

# 代码

~~~jsx
import React from "react"

export default function Form() {
    const [firstName, setFirstName] = React.useState("")
    
    function handleChange(event) {
        //console.log(event.target)
        // <input type="text" placeholder="First Name">
        // console.log(event.target.value)
        // 得到输入框的值
        setFirstName(event.target.value)
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                
                onChange={handleChange}
            />
        </form>
    )
}

~~~

### 说明

~~~jsx
console.log(event.target)
~~~

输出结果：

<input type="text" placeholder="First Name">

~~~jsx
console.log(event.target.value)
~~~

输出结果：

输入到input中的值

onChange事件：**当元素的值发生改变时**，会发生 onchange 事件