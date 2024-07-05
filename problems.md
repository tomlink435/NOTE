# 前端遇到的问题

node版本切换

# [error Resolve error: @vitejs/plugin-vue requires vue (>=3.2.13) or @vue/compiler-sfc to be present in the dependency tree](https://www.cnblogs.com/hailexuexi/p/17411989.html)

执行

```
npm install vue@3.2.13 --save-dev
```





## node版本切换

安装和切换node版本

列出所有node版本

$ n ls

安装某个版本

$ n xx.xx.x (xx.xx.x 为要安装的版本号)

安装最新版本

$ n lastest

安装最新稳定版

$ n stable

切换node版本(输入命令后上下键盘选择确认)

$ n

删除某个版本

$ n rm xx.xx.x

使用某个版本来运行脚本

$ n use xx.xx.x a.js



最终发现问题，还是node版本的原因，vue的原因。

### 切换python版本

1. **装`pyenv`**:
   - 在macOS上，可以使用Homebrew：`brew install pyenv`。
   - 在Linux或Windows的WSL上，可以参照`pyenv`的GitHub仓库中的安装指南。
2. **安装新的Python版本**:
   - 使用`pyenv install <version>`命令安装新版本的Python。例如：`pyenv install 3.8.10`。
3. **切换Python版本**:
   - 全局切换：`pyenv global 3.8.10`，将系统级别的Python版本切换到3.8.10。
   - 本地切换：在特定项目目录中使用`pyenv local 3.8.10`，这将在该目录中设置Python版本。

### MMPose遇到的问题

#### 没有cuda

将server文件中的cuda换成mps即可（花了15元请人搞定的）



## 改数据库密码

版本：mysql Ver 8.2.0 for macos13.5 on arm64 (Homebrew)

```\
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '12345678';
```



# docker 

pull不下来：

![image-20240606101929230](/Users/teresa/Library/Application Support/typora-user-images/image-20240606101929230.png)

`sudo mkdir -p /etc/docker sudo tee /etc/docker/daemon.json <<-'EOF' {  "registry-mirrors": ["https://c2b4txcf.mirror.aliyuncs.com"] } EOF sudo systemctl daemon-reload sudo systemctl restart docker`

修改镜像文件即可

进不去的问题，换一个映射端口即可http://120.55.182.185:8011/ss-admin/install/

Sscms超级管理员admin

密码jyvca8-vyrbiK-hurjaq



## 文件上传服务器并访问的流程

方法1（默认配置）:

通过SpringBoot通常访问静态资源的方式，当访问：项目根路径 + / + 静态文件名时，SpringBoot会依次去类路径下的四个静态资源目录下查找![image-20240702163648481](/Users/teresa/Library/Application Support/typora-user-images/image-20240702163648481.png)

有时候重启一下就好了

方法2:

配置资源映射文件

yml中![image-20240703092854775](/Users/teresa/Library/Application Support/typora-user-images/image-20240703092854775.png)

Myconfig  配置映射

```
@Override
public void addResourceHandlers(ResourceHandlerRegistry registry) {

    registry.addResourceHandler("/staticfiles/**")
            .addResourceLocations("file:"+uploadpath+"/");
  
}
```

前端

 item.imageUrl = BASE_URL + '/api/staticfiles/image/' + item.image

![image-20240703100257767](/Users/teresa/Library/Application Support/typora-user-images/image-20240703100257767.png)
