# Radio

1. input标签，类型是radio
2. 属性
   1. 它也需要id，为了于后面的文字内容（label标签捆绑）
   2. name （在一个方框中的（fieldset子标签下）name值是一样的）
   3. value （和其他input不同的是，它的value值是固定的和下面label标签内容一样）
   4. onChange
   5. checked，（**为了实现控制组件**）
      1. 总所周知，**checked是一个布尔值**，但是如果和checkbox中的checked写一样了（checked={formData.employment}）是不对的，因为formData.employment对应的是“Unemployed”，“Part-time” and “Full-time”，并不是布尔值，
      2. 所以我们对每一个checked写成checked={formData.employment === "unemployed"}（且“unemployed”为value值）

# 代码

~~~jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {
            isFriendly: true,
            employment: ""
        }
    )
    
    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [name]: type === "checkbox" ? checked : value
            }
        })
    }
    
    return (
        <form>
            
            <input 
                type="checkbox" 
                id="isFriendly" 
                checked={formData.isFriendly}
                onChange={handleChange}
                name="isFriendly"
            />
            <label htmlFor="isFriendly">Are you friendly?</label>
            <br />
            <br />
            
            <fieldset>
                <legend>Current employment status</legend>
                
                <input 
                    type="radio"
                    id="unemployed"
                    name="employment"
                    value="unemployed"
                    checked={formData.employment === "unemployed"}
                    onChange={handleChange}
                />
                <label htmlFor="unemployed">Unemployed</label>
                <br />
                
                <input 
                    type="radio"
                    id="part-time"
                    name="employment"
                    value="part-time"
                    checked={formData.employment === "part-time"}
                    onChange={handleChange}
                />
                <label htmlFor="part-time">Part-time</label>
                <br />
                
                <input 
                    type="radio"
                    id="full-time"
                    name="employment"
                    value="full-time"
                    checked={formData.employment === "full-time"}
                    onChange={handleChange}
                />
                <label htmlFor="full-time">Full-time</label>
                <br />
                
            </fieldset>
        </form>
    )
}
~~~

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob26.PNG

# 学习网站

https://scrimba.com/learn/learnreact/forms-in-react-radio-buttons-co14c423dbc2026a7a2b997a2