# 是什么

React是一个用于**构建用户界面的JavaScript库**

用户界面：HTML页面（前端）

React：构建web应用

# 特点

- 声明式
  - 你只需要描述UI（HTML）看起来是什么样子，就跟写HTML一样
  - React只负责渲染UI，并在数据变化时更新UI
- 基于组件
  - 是最重要的内容
  - 组件表示页面中的部分内容
  - 组合、复用多个组件，可以实现完整的页面功能
- 学习一次，随处使用
  - 使用React可以开发Web应用
  - 使用React可以开发移动端原生应用
  - 使用React可以开发VR应用

# 演示图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/React01.jpg

# react高效的原因

- 使用虚拟DOM，不总是直接操作页面真实DOM
- 在操作真实DOM之前也会将虚拟DOM进行比较，比较出有差异的部分进行渲染