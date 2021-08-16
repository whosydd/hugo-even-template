# Hugo + Vercel 轻松搭建个人博客

## 预览

![blog-even-hugo](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108151820998.jpg)

## 参考

Hugo 中文文档 https://www.gohugo.org/

Even 主题中文文档 https://github.com/olOwOlo/hugo-theme-even/blob/master/README-zh.md

## 搭建 Hugo 环境

### 安装 Hugo

github 下载地址：https://github.com/gohugoio/hugo/releases

> 如果你想要修改`themes/even/assets/`下的文件，请安装`extended`版本

### 设置环境变量

将解压后的文件夹添加到`环境变量`中的`系统变量`中的`Path`中

![Capture](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152146130.PNG)

![Capture1](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152148938.PNG)

### 测试

```bash
hugo env -v
```

打开终端，输入`hugo env -v`，输出如下图表示安装成功！

![Capture2](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152152033.PNG)

## 构建项目

> 如果此时你还没有 github 账号，请先[注册](https://github.com/)一个，方便进行后续操作
>
> 由于一些不可控因素，github 访问速度可能会很慢，[你可能会需要这个](https://keylol.com/t256816-1-1)
>
> 由于要使用 git 进行版本控制，如果还没有安装，请前往[这里](https://git-scm.com/)下载安装，使用`git --version`命令查看是否安装成功

### 项目结构

| 名称        | 说明                                           |
| ----------- | ---------------------------------------------- |
| archetypes/ | 放置内容模板，在创建新内容时会根据模板创建文章 |
| content/    | 博客内容，全部使用 markdown 格式               |
| layouts/    | 博客模板文件，决定内容如何呈现                 |
| static/     | 图片、css、js 等静态资源                       |
| themes/     | 存放主题                                       |
| config.toml | 项目的主配置文件(有的主题也会使用`config.yml`) |

### 使用模板构建项目

1. 只需要在[本仓库](https://github.com/whosydd/hugo-even-template)中点击`Use this template`，设置好仓库名称，就可以根据模板创建自己的项目仓库了
2. 使用`git clone <仓库地址>`到本地，或者直接下载压缩包，就可以构建本地项目了

![Screenshot of whosydd_blog_ 个人博客](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108161106992.jpg)

### 使用其他主题构建项目（可选）

#### 构建基本项目

```bash
hugo new site <项目名称>
```

#### 下载主题

1. 前往[这里](https://themes.gohugo.io/)下载主题，每个主题都会有相应的配置文档，请仔细阅读

#### 添加远程仓库

1. 点击`+`选择`New repository`创建新仓库

![Screenshot of GitHub](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152320408.jpg)

2. 给仓库起个名字，其他默认

![Screenshot of Create a New Repository](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152326277.jpg)

3. 获取远程仓库地址后，使用下面的命令将本地项目推送到 github

![Screenshot of whosydd_demo](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152348179.jpg)

```bash
#初始化仓库
git init

#添加远程仓库
git remote add origin <远程仓库地址>

#添加文件到暂存区
git add .

#提交commit
git commit -m 'init'

#推送
git push -u origin main
```

#### 血的教训：

**不知道由于何种原因，如果主题文件夹中保留`.git`文件夹，vercel 部署时 99.9%会报错！也就是说，只有将主题文件夹中的所有文件都交由主项目进行 git 管理才可以！**

> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！
>
> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！
>
> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！

## 配置选项

> 以下配置项仅针对[Even 主题](https://themes.gohugo.io/themes/hugo-theme-even/)，如果选择使用其他主题，请查阅相应的主题配置文档

### config.toml

这里仅仅是我**修改过的**配置项，请在项目根目录的`config.toml`中查看详细配置

```toml
# 这里设置成你博客的域名
baseURL = "http://www.whosydd.ml/"

# 设置默认显示语言，可选语言可以在themes/even/i18n/中查看
defaultContentLanguage = "zh-cn"

# 设置网站标签页显示的信息
title = "Blog - C'est la vie!"

# 设置作者
[author]
  name = "GY"

# 配置目录 （使用weight进行排序）
[[menu.main]]
  name = "主页"
  weight = 10
  identifier = "home"
  url = "/"
[[menu.main]]
  name = "标签"
  weight = 20
  identifier = "tags"
  url = "/tags/"
[[menu.main]]
  name = "类别"
  weight = 30
  identifier = "categories"
  url = "/categories/"
[[menu.main]]
  name = "归档"
  weight = 40
  identifier = "archives"
  url = "/post/"

# 设置站点建立时间
[params]
  since = "2021"

  # 是否在归档页显示文章的总数
  # 如果设置为false，则不会在主页显示文章的内容预览
  showArchiveCount = true

  # 这是我新添加的选项，设置为true时，会在主页中的每篇文章中显示阅读更多
  # show 'read more' link ?
  readMore = false

  # 是否显示文章中的页脚信息（包含作者，上次修改时间，markdown链接，许可信息）
  postMetaInFooter = false

  # 设置页脚中社交链接图标，你可以选择你想要显示的社交链接
  [params.social]
    a-email = "mailto:dev.youngkwok718@gmail.com"
    #b-stack-overflow = "http://localhost:1313"
    #c-twitter = "http://localhost:1313"
    #d-facebook = "http://localhost:1313"
    #e-linkedin = "http://localhost:1313"
    #f-google = "http://localhost:1313"
    g-github = "http://github.com/whosydd"
    #h-weibo = "http://localhost:1313"
    #i-zhihu = "http://localhost:1313"
    #j-douban = "http://localhost:1313"
    #k-pocket = "http://localhost:1313"
    #l-tumblr = "http://localhost:1313"
    #m-instagram = "http://localhost:1313"
    #n-gitlab = "http://localhost:1313"
    #o-bilibili = "http://localhost:1313"

```

### favicon 图标

你可以在[**这里**](https://favicon.io/favicon-generator/)创建 favicon 图标，然后将解压之后的**所有图标文件**放到项目根目录的`static/`中即可

![Screenshot of Favicon Generator - Text to Favicon - favicon.io](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152248657.jpg)

### 文章模板

- 可以在`themes/even/archetypes/`中找到文章模板，只需要将该文件复制一份，放到项目根目录中的`archetypes/`中即可。
- 建议只保留一些常用的配置项即可
- 其中的`Draft`配置项默认为`true`，表示该文章为草稿，发布时记得改为`false`
- 你可以在根目录的`content/post/`中查看所有的文章

## 本地调试

### 运行hugo

```bash
hugo server -D
```

> 不加`-D`时，不会显示`Draft`配置项设置为`true`的文章

### 新建文章

```bash
hugo new post/<文件名>.md
```

> 你可以在`content/post/`下查看新建的文章

### 推送到github

```bash
# 添加所有文件到暂存区
git add .

# 提交commit
git commit -m 'updated'

# push到github
git push
```

## vercel 部署

### 注册

vercel 注册地址：https://vercel.com/signup

一般情况下，建议使用 github 账号注册

### 新建项目

1. 点击`New Project`创建新项目

![Screenshot of Dashboard – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160008063.jpg)

2. 初次使用，这里应该会出现`install Vercel for Github`，按照流程安装即可

![Screenshot of Project Creation Flow – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160020169.jpg)

3. 点击上图中的链接会跳转到https://github.com/settings/installations页面，点击`Configur`进行配置

![Screenshot of Installed GitHub Apps](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160029136.jpg)

![Screenshot of Installed GitHub App - Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160033050.jpg)

4. 配置好后则可以选择相应的仓库，点击`Import`导入

![Screenshot of Project Creation Flow – Vercel (1)](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160046695.jpg)

5. 出现以下页面就表示部署成功了，点击`Go to Dashboard`进入管理页面

![Screenshot of Project Creation Flow – Vercel (2)](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160050186.jpg)

6. 如果页面不显示，请点击`View Build Logs`查看`Build Logs`了解详情

![Screenshot of hugo-even-template – Overview – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108161158580.jpg)

### 配置项目

![Screenshot of demo – Overview – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160100546.jpg)

#### 添加自定义域名

##### 注册域名

你可以在https://my.freenom.com/注册一个长达12个月的免费域名，不过这个网站大陆访问有点慢

> 请注意：这里使用免费域名仅为了演示，如果有需求，建议直接[阿里云](https://wanwang.aliyun.com/?spm=5176.19720258.J_8058803260.153.e9392c4anmPBf1)购买域名

##### 添加域名

1. 在此页面输入已注册的域名，会弹窗让你选择重定向，选择`Recommended`的即可

![Screenshot of demo – Domains – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160105923.jpg)

##### 域名解析

这里建议直接选择 Nameservers，然后根据提示将`ns1.vercel-dns.com`和`ns2.vercel-dns.com`添加到注册域名网站的相关配置中，然后点击`Refresh`刷新状态，如果都打钩了就可以了，此时就可以通过你填写的域名访问博客了

> 以https://my.freenom.com/注册的域名为例：注册成功后，需要在主页依次点击`Services -> My Domains -> Manage Domain -> Management Tools -> Nameservers`，选择`Use custom nameservers`，添加`ns1.vercel-dns.com`和`ns2.vercel-dns.com`即可

![Screenshot of demo – Domains – Vercel (2)](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160134606.jpg)

### 删除项目

`Settings -> Advanced -> Delete Project`

![Screenshot of demo – Advanced – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160147843.jpg)

### 自动部署

只要第一次部署成功后，以后只需要将本地新写的文章推送到 github 即可，vercel 会在每次 commit 后自动部署

## 最后

由于hugo我也是刚刚接触，所以只是简单配置了一下，还有很多地方都不够完善。如果发现有哪里写的不好或者不对的地方，欢迎 pr~

**C'est la vie!**
