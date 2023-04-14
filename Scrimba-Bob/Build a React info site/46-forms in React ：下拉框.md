#  select

1. 标签属性
   1. name
   2. value
   3. onChange
   4. id

# 代码

~~~jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {
            favColor: ""
            
        }
    )
    //解决一个问题，如果我们刷新页面，初始状态是空
    //<option value="">-- Choose --</option>
    console.log(formData.favColor)
    
    function handleChange(event) {
        console.log(event)
        const {name, value } = event.target
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [name]:  value
            }
        })
    }
    
    return (
        <form>
            <label htmlFor="favColor">What is your favorite color?</label>
            <br />
            <select 
                id="favColor"
                value={formData.favColor}
                onChange={handleChange}
                name="favColor"
            >
                <option value="">---chose---</option>   //为了避免刷新页面由于最开始没有选择，使得formData.favColor为空
                <option value="red">Red</option>
                <option value="orange">Orange</option>
                <option value="yellow">Yellow</option>
                <option value="green">Green</option>
                <option value="blue">Blue</option>
                <option value="indigo">Indigo</option>
                <option value="violet">Violet</option>
            </select>
        </form>
    )
}

~~~

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob28.PNG

# 学习网站

https://scrimba.com/learn/learnreact/forms-in-react-select-option-co83b466d859cf1d6c4b3efaf