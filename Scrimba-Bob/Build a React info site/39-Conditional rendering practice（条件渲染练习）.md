# 需求

Challenge:

​      If there are no unread messages, display "You're all caught up!"

​      If there are > 0 unread messages, display "You have <n> unread message(s)"

​           - If there's exactly 1 unread message, it should read "message" (singular)

# 代码

~~~jsx
import React from "react"

export default function App() {
    const [messages, setMessages] = React.useState(["a", "b"])
   
    return (
        <div>
            {
                messages.length ?
                <h1>You have {messages.length} unread {
                    messages.length === 1?
                    "message" : "messages"
                }</h1> :
                <h1>You're all caught up!</h1>
            }
        </div>
    )
}
~~~

# 运行结果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob21.PNG

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob22.PNG

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob23.PNG