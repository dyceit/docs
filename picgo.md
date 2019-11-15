# PicGo

## 创建 GitHub 图床仓库

1. 创建 [GitHub][1] 图床之前，需要注册 / 登陆  [GitHub][1] 账号

2. 进入 [GitHub][1] 首页，点击 "New" 创建 Repository

![](https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114131738.png)

- 按步骤完成下面操作

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114130639.png" style="zoom:67%;" />

3. 生成一个 Token 用于操作 GitHub repository

- 进入 "Settings" 页面后，点击 "Developer settings" 按钮

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114132224.png" style="zoom: 50%;" />

- 点击 "Personal access tokens" 按钮

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114132344.png" style="zoom: 50%;" />

- 创建新的 Token

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114132410.png" style="zoom:50%;" />

- 填写描述，选择 "repo", 然后点击 "Generate token" 按钮

> 注：创建成功后，会生成一串 token，这串 token 之后不会再显示，所以第一次看到的时候，就要好好保存

## PicGo 安装与配置

1. 进入 https://github.com/Molunerfinn/PicGo 下载安装 PicGo

进入 https://github.com/Molunerfinn/PicGo 下载安装 PicGo

2. 如图配置 GitHub 图床

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114134812.png" style="zoom:50%;" />

* 仓库名“账户名 / 仓库名”的格式填写
* 分支名统一填写 “master”
* 将之前的 Token 黏贴在这里
* 存储的路径设置后，就会在 repository 下自动创建一个 “markd存储的路径设置后，就会在 repository 下自动创建一个 “markdmarkdown*own” 文件夹
* 自定义域名的作用是，在上传图片后成功后，PicGo 会将 “自定义域名 + 上传的图片名” 生成的访问链接，放到剪切板上https://raw.githubusercontent.com/用户名/RepositoryName/分支名，自定义域名需要按照这样去填写

3. 安装完成后进入 “PicGo设置”，选择 GitHib 图床。如有其它图床，按需求设置即可。

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114133854.png" style="zoom:50%;" />

4. 将上传完成后生成的图片地址设置成 Markdown 格式

<img src="https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114134339.png" style="zoom:50%;" />

5. 上传完成后自动将图片地址复制到剪贴板

- 可拖动上传

![](https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114134023.png)

- 也可以截图后，点击待上传里的图片上传

![](https://raw.githubusercontent.com/dyceit/graph-bed/master/markdown/20191114134225.png)

6. 剪贴板直接粘贴到 Markdown 编辑器，就那么简单。

[1]: https://github.com/

