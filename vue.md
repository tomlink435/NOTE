js框架，两种书写风格



es6是规范，js是实现



## 编程式和声明式和命令式的区别

声明式关注结果（sql）

编程式将函数作为主（List<Integer> result = collation.stream().filter(num -> num > 3).collect(Collectors.toList());）

命令式关注步骤（平时常见，做饭步骤）



## Vue2 和 vue3 的区别

1. Vue3提供了全新的Composition API来替代以前的Options API,[ Script](https://geek-docs.com/vuejs/vue-js-questions/939_vuejs_how_do_you_export_default_from_inside_script_setup_in_vue_3.html#) setup是Composition API的核心之一，它使得编写Vue组件更加简洁和直观。
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

1. 无参数

   `<router-link :to="{name: 'home' }" > </router-link>
   <router-link :to="{path: '/home'}" > </router-link>
   // name, path都行, 建议用name 
   <router-link :to="{name: 'home'}" tag='li'> </router-link>`

   1. `<router-link>` 中链接如果是 `/` 开始就是从根路由开始，如果开始不带 `/`，则从当前路由开始。
   2. `<router-link>` 会默认解析成 `a` 标签，可以通过 `tag` 属性指定它解析成其他标签

2. 声明式

   1. params

```<router-link :to="{name:'home, params: {id:1}'}"></router-link>```

刷新页面参数消失（除非配置path）

 html取参: $route.params.id 

 script取参: this.$route.params.id

	2. query方式传参：
	<router-link :to="{name: 'home', query: {id:1}}"> 
	// query传参数 (类似get, url后面会显示参数)
	// 路由可不配置
	// html取参: $route.query.id
	// script取参: this.$route.query.id
	
	query 和 params 区别
	
	query 类似 get，跳转之后页面 url 后面会拼接参数，类似 ?id=1，非重要性的可以这样传，密码之类还是用 params 刷新页面 id 还在；
	params 类似 post，跳转之后页面 url 后面不会拼接参数，但是刷新页面 id 会消失。

3. 编程式

   ##### `this.$router.push()`

   query

   `this.$router.push({name:'home', query: {id:'1'}})
   this.$router.push({path:'/home',query: {id:'1'}})
   // html取参: $route.query.id
   // script取参: this.$route.query.id`

   params

   ``this.$router.push({name:'home',params: {id:'1'}})
   // 只能用 name
   // 路由配置path: "/home/:id" 或者 path: "/home:id",
   // 不配置path, 第一次可请求, 刷新页面id会消失
   // 配置path, 刷新页面id会保留
   // html取参, $route.params.id
   // script取参, this.$route.params.id``

##### `this.$router.back()`返回上一个路由

##### `this.$router.go(n)`向前或向后跳转n个页面（正负数）





Router.resolve新窗口打开，只支持query

`let data = this.$router.resolve({
  path: "/channel_sms",// 或者 name: 'channel_sms',
  query: {
    a: 1,
  },
});`





push当前窗口打开，支持query和params



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



## ts和js的区别

ts是js的超集



## 什么是Script Setup?

[ Script](https://geek-docs.com/vuejs/vue-js-questions/939_vuejs_how_do_you_export_default_from_inside_script_setup_in_vue_3.html#) setup不需要再使用export default来导出组件选项，它会自动将脚本中的所有变量、函数和组件选项导出。

```vue
<script setup>
  // 在此处编写组件的脚本逻辑
</script>
```





## 路由对象传参（重要）

传参页面

router.**push**({ name: 'done', query: { form: JSON.**stringify**(form) } });



跳转页面

 const formQuery = route.query.form;

​      if (formQuery) {

​        **Object**.**assign**(form, JSON.**parse**(formQuery));

​      }

​      console.**log**('-----', form);







### npm install 权限

在 Windows 系统中，打开命令提示符，右键以管理员身份运行，然后再运行 npm install 即可获得**管理员权限**。 在 macOS 和 Linux 系统中，打开终端，使用 sudo 命令运行 npm install ，例如： sudo npm install 。







# js

![image-20240728162116167](/Users/teresa/Library/Application Support/typora-user-images/image-20240728162116167.png)



# 跨域

![image-20240728171854141](/Users/teresa/Library/Application Support/typora-user-images/image-20240728171854141.png)



---

# token

![image-20240728174002312](/Users/teresa/Library/Application Support/typora-user-images/image-20240728174002312.png)









