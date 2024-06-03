# 是什么

 Python 网络框架，可以快速开发安全和可维护的网站

# 为什么用

毕设

# 怎么用

## 创建工程

terminal：django-admin.py startproject mytest

**如果你的桌面没有生成mytest文件夹**，但是pycharm却启动了，那么尝试一下terminal：django-admin startproject mytest（我就是这种情况）

![image-20240124154655549](/Users/teresa/Library/Application Support/typora-user-images/image-20240124154655549.png)

__init__.py：表明该目录为一个python包
***setting.py：项目设置文件、数据库配置***
***urls.py：URL映射管理***
manage.py：对项目进行操作的命令
wsgi.py：Python Web Server Gateway Interface，是Python应用程序或框架和Web服务器之间的一种接口。

## 启动工程

进入mytest目录后，执行：`python manage.py runserver`，来启动django的自带Web服务器。

打开网址 http://127.0.0.1:8000/ 

![image-20240124155003198](/Users/teresa/Library/Application Support/typora-user-images/image-20240124155003198.png)

success！

## 创建app

这个app是各种功能，用来实现各种业务，每个app的表结构、函数、HTML模板、css等都可以分开管理，不会混乱。

输入指令`python manage.py startapp app名`（通过manage.py来创建app），以下是创建的test1

 ![image-20240124160201521](/Users/teresa/Library/Application Support/typora-user-images/image-20240124160201521.png)

目录结构：

​     |  admin.py				【固定的不用动】django默认提供的后台管理，但实际开发不常用
​    │  apps.py				【固定的不用动】app启动相关
​    │  **models.py**			【☆很重要，对数据库进行操作】这里不用SQL写了，Django封装了ORM供调用
​    │  tests.py				【固定的不用动】用来单元功能测试的，个人小项目可以不用管
​    │  **views.py**				【☆很重要，撰写视图函数（得我们自己写的）】
​    │  init.py
​    └─migrations			【固定的不用动】数据库变更记录，会自动生成文件，我们不用动
​            init.py

## 快速上手

### 注册app

我们得让Django知道，我们写了一个新app，此过程需要修改settings.py

![image-20240124162640146](/Users/teresa/Library/Application Support/typora-user-images/image-20240124162640146.png)

![image-20240124162623159](/Users/teresa/Library/Application Support/typora-user-images/image-20240124162623159.png)

### URL和函数的映射

使用网站时，在网站内的页面跳转都会改变URL，不同的URL就需要后台调用不同的功能给用户使用。所以每个URL都得有函数来执行相应的代码。此过程需要修改**urls.py**

找到urls.py中列表变量urlpatterns，添加一行`path('', )`

![image-20240124163046130](/Users/teresa/Library/Application Support/typora-user-images/image-20240124163046130.png)

`path()`需要两个参数，前者是字符串，规定URL，后者是触发的函数名。(规定的URL可以随便写

每个app都有个`views.py`，里面是写函数的，所以我们第二个参数位导入相应函数即可

```
urlpatterns = [
    path('test1/',views.func1)
]
```

### 视图函数的撰写

这个过程需修改相应app下的views.py

![image-20240124164041309](/Users/teresa/Library/Application Support/typora-user-images/image-20240124164041309.png)

1. django中的视图函数必须带request这个参数

2. 视图函数必须return，一般返回的都是要传给前端的数据

3. 这里的 HttpResponse()先简单理解为给前端发简单数据的，后面是得传 html文件给前端的，不怎么用 HttpResponse()的。

### 运行Django

命令行输入 python manage.py runserver

http://127.0.0.1:8000/test1/

![image-20240124164642466](/Users/teresa/Library/Application Support/typora-user-images/image-20240124164642466.png)

那我们现在如果还要创建新的页面，只需要两个步骤：

1. views.py中撰写相应函数
2. urls.py中定义URL和函数的对应关系

## 模板文件&静态文件

### render()使用

But，正常应用中，网页都得是html那些文件，我们这现在还是就单纯返回字符串，太单调了。

那我们return后面就不用`HttpResponse()`了，而是用`render()`。`render()`的用法是这样。

``` 
def user_list(request):
    return render(request, "user_list.html")# 第一个位子是视图函数的request参数，第二个参数位是html文件路径
```

### 模板路径问题

在app下创建名为`templates`的文件夹（必须得为templates，不要拼写错误！），并在`templates`文件夹下创建html文件。

![image-20240124192655577](/Users/teresa/Library/Application Support/typora-user-images/image-20240124192655577.png)

![image-20240124192627741](/Users/teresa/Library/Application Support/typora-user-images/image-20240124192627741.png)

## Django模板语法

### 调用后端数据

`render()`函数第三个参数位可以提供给视图函数传递数据，不过第三个参数必须是字典！

views.py

```
def func2(request):
    name="teresa"
    students=['s1','s2','s3']
    return render(request,'html1.html',{"n1":name,"stu_list":students})
```

Html:

```
<h1>模板语法学习</h1>
<div>{{n1}}</div>
<div>{{stu_list}}</div>
```

![image-20240125145134518](/Users/teresa/Library/Application Support/typora-user-images/image-20240125145134518.png)

## Request&Response

### request

request就是一个对象，封装了用户通过浏览器发过来的所有数据

- `request.method`：获取用户请求提交方式（GET/POST）
- `request.GET`：获取通过URL传递的参数
- `request.POST`：通过请求体中获得数据

### response

- `HttpResponse()`：返回内容字符串给请求者；
- `render()`：读取HTML，并渲染，最终以字符串的格式返回给用户浏览器；
- `redirect()`：让浏览器重定向到其他页面，返回的是网址。

重定向的过程：

浏览器提交请求给django，django收到请求后将请求直接提交给重定向的网址，浏览器去新的网址提交请求，新的网址给浏览器返回数据

## 数据库操作 ORM

在Django开发中，我们不需要在手动去写了，django给我们封装好了，并且增加了安全机制，让用户更简单更安全的操作数据库。这个封装好的东西就是ORM。

### 安装第三方模块

Pip3 install mysqlclient

##### 问题记录

提示需要wheel

可以通过 `env` 设置环境变量指定依赖库的位置：

env LDFLAGS="-L/opt/homebrew/Cellar/zstd/1.5.0/lib" pip install mysqlclient==1.4.4

success！

### ORM

ORM可以帮助我们做两件事：

- 增删改查数据库中的表（不用写SQL语句）【但数据库你得自己建】
- 操作表中数据，即增删改查表中记录（不用写SQL语句）

### django连接数据库

只需要在`settings.py`文件中配置连接参数即可

``` 'default': {
    'ENGINE': 'django.db.backends.mysql',	# Django的引擎，还可以用Oracle等
    'NAME': 'dbname',	# 数据库名
    'USER': 'root',		# 用户名
    'PASSWORD': 'xxx',	# 密码
    'HOST': '',			# 数据库服务器地址
    'PORT': 3306,		# 端口号（MySQL默认3306）
}
```

### django操作表

#### 增

在相应app中的***models.py***中写一个类就是创建一张表。

```
# 在MySQL中创建对应的一个表
class UserInfo(models.Model):
    # 创建字段
    name = models.CharField(max_length=32)
    password = models.CharField(max_length=64)
    age = models.IntegerField()
```

ORM会帮我们把这个面向对象的代码转化成SQL（表名是app名称_类名），与上面代码对应的SQL大致为：

```create table index_userinfo(
create table index_userinfo(
    id bigint auto_increment primary key,		【django创建表自带自增字段】
    name varchar(32),
    password varchar(64),
    age int,
);
```

到terminal界面下执行命令，通过`manage.py`来让ORM读取我们写好的models.py中的代码

```python manage.py makemigrations
python manage.py makemigrations
python manage.py migrate
```





#### 删

#### 改

#### 查





# 登陆功能

## 前端

```
<!--suppress ALL -->
<template>
      <div class="login">
        <div class="loginPart">
          <h2>用户登录</h2>
          <!-- 登录主体，表单 -->
          <el-form  ref="loginFormRef" :model="loginForm" :rules="loginFormRules" label-width="0px" style="margin-top: 5px;">
            <!-- 用户名 -->
            <div>
              <el-form-item prop="username" class="inputElement">
                <el-input type="text" v-model="loginForm.username" placeholder="用户名" :prefix-icon="User"></el-input>
              </el-form-item>
            </div>


            <!-- 密码 -->
            <el-form-item prop="password" class="inputElement">
              <el-input type="password" v-model="loginForm.password" placeholder="密码" :prefix-icon="Lock"></el-input>
            </el-form-item>

            <!-- 按钮 -->
            <el-form-item>
              <el-button type="primary" @click="handleLogin" style="margin-left: 40%">登录</el-button>
            </el-form-item>
          </el-form>
        </div 
      </div>
</template>

<script lang="ts" setup>
import {reactive, ref} from "vue"
import axios from "axios";
import { useRouter } from "vue-router"
import {ElLoading} from "element-plus";
import { User, Lock } from "@element-plus/icons-vue"
import { type FormInstance, FormRules } from "element-plus"
import {decode, encode} from "js-base64";
import jsCookie from "js-cookie"
import { usePermissStore } from '../store/permiss';

const permiss = usePermissStore();
const loginFormRef = ref<FormInstance | null>(null)
const router = useRouter()
//登录表单
const loginForm = reactive({
  username: "",
  password: "",
})

//登录校验规则
const loginFormRules: FormRules = {
  username: [{ required: true, message: "请输入用户名", trigger: "blur" }],
  password: [
    { required: true, message: "请输入密码", trigger: "blur" },
    { min: 5, max: 16, message: "长度在 5 到 16 个字符", trigger: "blur" }
  ],
}

//登录逻辑
const handleLogin = ()=>{
  const loading = ElLoading.service({
    lock: true,
    text: '进入标注系统......',
    background: 'rgba(255,255,255, 1)',
  })
  //表单验证
  loginFormRef.value?.validate((valid: boolean) => {
    if (valid) {
      //发起登录请求
      axios.post("/api/sign/signIn/", {
        userName:loginForm.username,
        password:loginForm.password,
      }).then((res) => {
        res = JSON.parse(res)
        //权限信息

        //页面跳转
        if (res.role=='1'||res.role=='2'){
          const keys = permiss.defaultList[res.role == '1' ? 'admin' : 'user'];
          permiss.handleSet(keys);
          localStorage.setItem('ms_keys', JSON.stringify(keys));

          //存储用户信息
          localStorage.setItem("userId", res.id);
          localStorage.setItem("userName", res.username);
          localStorage.setItem("role", res.role);
          router.push("/")
        }

      })
    }else{
      return false
    }

})
  loading.close()
}
</script>

<style lang="scss" scoped>
.loginPart{
  position:absolute;
  /*定位方式绝对定位absolute*/
  top:50%;
  left:50%;
  /*顶和高同时设置50%实现的是同时水平垂直居中效果*/
  transform:translate(-50%,-50%);
  /*实现块元素百分比下居中*/
  width:450px;
  padding:50px;
  background: rgba(0,0,0,.5);
  /*背景颜色为黑色，透明度为0.8*/
  box-sizing:border-box;
  /*box-sizing设置盒子模型的解析模式为怪异盒模型，
  将border和padding划归到width范围内*/
  box-shadow: 0px 15px 25px rgba(0,0,0,.5);
  /*边框阴影  水平阴影0 垂直阴影15px 模糊25px 颜色黑色透明度0.5*/
  border-radius:15px;
  /*边框圆角，四个角均为15px*/
}
.loginPart h2{
  margin:0 0 30px;
  padding:0;
  color: #fff;
  text-align:center;
  /*文字居中*/
}
.inputElement{
  margin-left: 15%;
}
.login{
  background-image: url("../assets/img_1.png");
  width:100%;
  height:100%;
}
</style>

```

























# 参考

https://blog.csdn.net/weixin_44293949/article/details/113071069

https://blog.csdn.net/Ans_min/article/details/123146335?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170608265216800222851232%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170608265216800222851232&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-123146335-null-null.142^v99^pc_search_result_base1&utm_term=django使用&spm=1018.2226.3001.4187 

1.24-1.25