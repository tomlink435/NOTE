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
