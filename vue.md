js框架，

两种书写风格



es6是规范，js是实现

## Vue2 和 vue3 的区别

1. 构建方式不同

webpack 

vite

2. main.js

引入构造函数

结构形式，引入工厂函数，app没有根标签

3. setup（） 
4. vue2可以直接使用slot，vue3需要v-slot



## 生命周期

vue2           ------->      vue3

beforeCreate   -------->      setup(()=>{})
created        -------->      setup(()=>{})
beforeMount    -------->      onBeforeMount(()=>{})
mounted        -------->      onMounted(()=>{})
beforeUpdate   -------->      onBeforeUpdate(()=>{})
updated        -------->      onUpdated(()=>{})
beforeDestroy  -------->      onBeforeUnmount(()=>{})
destroyed      -------->      onUnmounted(()=>{})
activated      -------->      onActivated(()=>{})
deactivated    -------->      onDeactivated(()=>{})
errorCaptured  -------->      onErrorCaptured(()=>{})





## 路由传参





## export default

用于导出常量、函数、文件、模块

是es6语言

一个文件只能有一个export default语句，是吧所有{}的内容赋给default







## ref和reactive 都是vue3响应式系统的基础

ref 把数据变成了响应式数据（a数据变更，所有a都变更），re把他们变成对象，需要用到.value

let name =ref('vvv')

let age=ref(18)

调用ref的时候自动调用reactive

#### 区别

ref基本数据类型，操作要.value，读取不要

reactive定义对象或者数组，不需要.value

#### vue3中的reactive

将普通对象转成响应式对象





