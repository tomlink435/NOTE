

## 基本操作

登录

```git config --global user.name 'tomlink435'  ```

` git config --global user.email '1484228340@qq.com'`

与远程仓库建立连接

```git remote add origin https://github.com/username/repository.git```

修改远程仓库地址

 ```git remote set-url origin https://github.com/yourname/learngit.git```

拉代码

```git pull origin master```

添加

```git add example.txt```

`git add .`

提交

`git commit -m "Update example.txt with new content"`

推送

`git push origin master`





## 配置密码存储

生成SSH秘钥

$ ssh-keygen -t rsa -C "1484228340@qq.com"

输入保存秘钥的文件路径（/Users/teresa/.ssh/id_rsa）和密码（020227）

![image-20240701115829970](/Users/teresa/Library/Application Support/typora-user-images/image-20240701115829970.png)

### 配置公钥

将公钥配置到你的远程[ 仓库](https://geek-docs.com/git/git-questions/1653_git_configuring_user_and_password_with_git_bash.html#)中，以便进行秘钥[ 认证](https://geek-docs.com/git/git-questions/1653_git_configuring_user_and_password_with_git_bash.html#)。

使用`cat`命令查看公钥文件内容

```bash
$ cat ~/.ssh/id_rsa.pub
```

生成内容：

//已删，否则因为这些信息git提交不上去



打开github设置，复制到ssh key上

命令行配置

git config --global user.email "1484228340@qq.com"
git config --global user.name "tomlink435"
git config --global core.sshCommand "ssh -i ~/.ssh/id_rsa"



## git实现忽略文件

定义.gitignore文件



## git rm操作后文件恢复

https://blog.csdn.net/wuqingshan2010/article/details/103631146





#### 为什么文件夹有白色箭头并且打不开

被认为是子模块，删除文件夹内的.git文件 

参考https://www.jianshu.com/p/28e61a24d847
