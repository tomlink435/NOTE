# 在Mac上安装和配置Anaconda

相对直接。以下是一个简单的步骤指南：

### 下载和安装

1. **访问Anaconda网站**: 前往 Anaconda官方网站 下载页面。
2. **选择Mac版本**: 选择适用于Mac的Anaconda版本（通常是一个.pkg安装文件）。
3. **下载**: 点击下载按钮开始下载。
4. **安装**: 下载完成后，双击.pkg文件启动安装程序。遵循安装程序中的指示完成安装。

### 初始配置

安装完成后，你可以进行一些基础的配置：

1. **打开终端**: 打开你的Mac上的终端（Terminal）。

2. **检查安装**: 输入以下命令来验证Anaconda是否正确安装：

   ```
   bashCopy code
   conda list
   ```

   这将列出已安装的包，表示Anaconda已经安装成功。

3. **更新Anaconda**: 为了确保所有的包都是最新的，可以执行以下命令：

   ```
   bashCopy code
   conda update --all
   ```

4. **创建环境** (可选): 你可以创建一个新的环境来隔离项目的依赖。例如，创建一个名为`myenv`的环境，并安装Python 3.8，可以使用：

   ```
   bashCopy code
   conda create -n myenv python=3.8
   ```

5. **激活环境**: 使用以下命令激活你的新环境：

   ```
   bashCopy code
   conda activate myenv
   ```

6. **开始使用**: 一旦环境被激活，你就可以开始安装需要的包并运行Python代码了。



# Conda虚拟环境

是一个非常强大的功能，它允许用户在隔离的环境中安装和运行不同的Python版本和库，而不会影响其他环境或操作系统上的Python安装。这对于管理依赖、避免版本冲突以及确保项目的可复制性非常重要。

### 创建新的虚拟环境

要创建一个新的Conda虚拟环境，你可以使用以下命令：

```
bashCopy code
conda create -n [环境名] python=[版本号]
```

例如，创建一个名为`myenv`的环境并安装Python 3.8，你可以使用：

```
bashCopy code
conda create -n myenv python=3.8
```

### 激活和退出虚拟环境

- **激活环境**: 使用以下命令来激活环境：

  ```
  bashCopy code
  conda activate myenv
  ```

- **退出环境**: 当你完成工作，要退出虚拟环境时，使用：

  ```
  bashCopy code
  conda deactivate
  ```

### 管理环境

- **查看所有环境**: 要列出所有可用的Conda环境，使用：

  ```
  bashCopy code
  conda env list
  ```

- **删除环境**: 要删除一个环境，使用：

  ```
  bashCopy code
  conda env remove -n myenv
  ```

### 管理环境中的包

在激活的环境中，你可以使用Conda或pip来安装、更新或删除包。

- **安装包**:

  ```
  bashCopy code
  conda install [包名]
  ```

- **更新包**:

  ```
  bashCopy code
  conda update [包名]
  ```

- **删除包**:

  ```
  bashCopy code
  conda remove [包名]
  ```

### 导出和导入环境

- **导出环境**: 你可以将环境的当前状态导出到一个YAML文件中，这对于共享环境配置非常有用。使用：

  ```
  bashCopy code
  conda env export > environment.yml
  ```

- **导入环境**: 要从YAML文件创建环境，使用：

  ```
  bashCopy code
  conda env create -f environment.yml
  ```

Conda虚拟环境是Python项目管理中一个非常实用的工具，它有助于确保开发环境的一致性和项目的可移植性。



#### 进入jupyter

https://www.bilibili.com/video/BV1hE411t7RN/?p=5&vd_source=864ac840fe8511f3101410cf04912a64

![Screenshot 2024-01-13 at 10.34.26](/Users/teresa/Desktop/Screenshot 2024-01-13 at 10.34.26.png)



```
img_path='/Users/teresa/Program/Code/pytorchTest/dataset/train/ants/5650366_e22b7e1065.jpg'

from PIL import Image

img=Image.open(img_path)

img.show()
```



![Screenshot 2024-01-15 at 10.30.47](/Users/teresa/Library/Application Support/typora-user-images/Screenshot 2024-01-15 at 10.30.47.png)

img->toTensor

transform

Img.open

tensorboard