# 需求

给29中App.js中的

~~~jsx
<img 
     src={`../images/${starIcon}`} 
     className="card--favorite"
     onClick={toggleFavorite}
/>
~~~

写成一个子组件

# 代码

### App.js

~~~jsx
import React from "react"
import Star from "./Star"

export default function App() {
    const [contact, setContact] = React.useState({
        firstName: "John",
        lastName: "Doe",
        phone: "+1 (719) 555-1212",
        email: "itsmyrealname@example.com",
        isFavorite: true
    })
    
    function toggleFavorite() {
        setContact(prevContact => ({
            ...prevContact,
            isFavorite: !prevContact.isFavorite
        }))
    }
    
    return (
        <main>
            <article className="card">
                <img src="./images/user.png" className="card--image" />
                <div className="card--info">
                    <Star isFilled={contact.isFavorite} handleClick={toggleFavorite} />
                    <h2 className="card--name">
                        {contact.firstName} {contact.lastName}
                    </h2>
                    <p className="card--contact">{contact.phone}</p>
                    <p className="card--contact">{contact.email}</p>
                </div>
                
            </article>
        </main>
    )
}

~~~

### Star.js

~~~jsx
import React from "react"

export default function Star(props) {
    const starIcon = props.isFilled ? "star-filled.png" : "star-empty.png"
    return (
        <img 
            src={`../images/${starIcon}`} 
            className="card--favorite"
            onClick={props.handleClick}
        />
    )
}
~~~

#### 自己第一次写的错误点：

~~~jsx
<Star isFilled = {contact.isFavorite} onClick = {toggleFavorite}/>
~~~

写成了上述的代码

不能这样写的原因：

 **不能直接给Star组件添加onClick功能**，这个**点击事件是给HTML标签**添加的，这个Star是我们自己创建的组件，如果我们写onClick = {toggleFavorite}，他不是一个点击事件，而是一个属性，所以我们需要给Star组件设置一个属性，来传递toggleFavorite



所以，给child component写点击事件的时候，需要一个**属性**来传递**被写在父组件的点击函数**



# 学习网址

https://scrimba.com/learn/learnreact/setting-state-from-child-components-co5104ccd8360769343dc8e51
