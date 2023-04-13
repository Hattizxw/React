# 需求

点击星星图片，可以将空星的图片换成实心的

# 运行结果图

### 初始状态

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob12.PNG

### 结束状态

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob13.PNG

# 代码

人的信息都按照对象的存储方式存储的

~~~jsx
import React from "react"

export default function App() {
    const [contact, setContact] = React.useState({
        firstName: "John",
        lastName: "Doe",
        phone: "+1 (719) 555-1212",
        email: "itsmyrealname@example.com",
        isFavorite: true
    })
    
    //设计带星图片和不带星图片的路径
    //如果isFavorite的值是true那就是fill，否则就是empty
    let starIcon = contact.isFavorite ? "star-filled.png" : "star-empty.png"
    
    function toggleFavorite() {
        setContact (prevState => {
            //返回一个对象
            return {
                ...prevState,
                isFavorite: !prevState.isFavorite
            }
        })
    }
    
    return (
        <main>
            <article className="card">
                <img src="./images/user.png" className="card--image" />
                <div className="card--info">
                    <img 
                        src={`../images/${starIcon}`} 
                        className="card--favorite"
                        onClick={toggleFavorite}
                    />
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

### 解析

在对象中面临的一个问题就是，在初始化的对象数据中，前面四个对象数据都不变，如何让setContact中只改变最后一个数据值

~~~jsx
function toggleFavorite() {
        setContact (prevState => {
            //返回一个对象
            return {
                ...prevState,
                isFavorite: !prevState.isFavorite
            }
        })
    }
~~~

其实（...prevState）

把所有的属性都放到了这里

这样就会有两个isFavorite的值，

但是React会获取最新的值，那就是（isFavorite: !prevState.isFavorite）

### css

~~~css
* {
    box-sizing: border-box;
}

body {
    background-color: whitesmoke;
    margin: 0;
    font-family: "Inter", sans-serif;
}

main {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.card {
    width: 200px;
    border: 1px solid lightgray;
    border-radius: 10px;
    height: 350px;
    box-shadow: 5px 5px 5px 1px rgba(120,120,120,0.44);
    -webkit-box-shadow: 5px 5px 5px 1px rgba(120,120,120,0.44);
    -moz-box-shadow: 5px 5px 5px 1px rgba(120,120,120,0.44);
}

.card--image {
    width: 100%;
    padding: 10%;
    padding-bottom: 0;
}

.card--name {
    margin-block: 13px;
    color: #333333;
}

.card--info {
    padding: 10px;
}

.card--favorite {
    width: 25px;
    cursor: pointer;
}

.card--contact {
    font-size: 0.75rem;
    color: gray;
    margin-block: 7px;
}
~~~

