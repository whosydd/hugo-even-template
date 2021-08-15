# Hugo + Vercel 轻松搭建个人博客

## 预览

![blog-even-hugo](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108151820998.jpg)

## Hugo 中文文档 https://www.gohugo.org/

> 如果在安装或者配置时遇到问题，可以参考此文档

## 搭建 Hugo 环境

### 安装 Hugo

github 下载地址：https://github.com/gohugoio/hugo/releases

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

> 如果此时你还没有 github 账号，请先注册一个，方便进行后续操作
>
> 注册地址：https://github.com/

### 使用 hugo 创建基本项目

```bash
hugo new site 项目名称
```

#### 项目结构

| 名称        | 说明                                           |
| ----------- | ---------------------------------------------- |
| archetypes/ | 包括内容类型，在创建新内容时自动生成内容的配置 |
| content/    | 网站内容，全部使用 markdown 格式               |
| layouts/    | 网站模板文件，决定内容如何呈现                 |
| static/     | 图片、css、js 等静态资源                       |
| themes/     | 存放主题                                       |
| config.toml | 项目的主配置文件(也可以使用`config.yml`)       |

### 使用主题

- 想要搭建一个美观的博客，最简单的方式就是使用主题，你可以在[这里](https://themes.gohugo.io/)浏览你想要的主题

- 找到想要的主题后，进入该主题页面，可以查看该主题的介绍以及使用方法，点击`Download`按钮可以跳转到 github 进行安装。

  > 建议仔细查看主题的使用方法，一般都会提供相应的配置模板，如果页面中没有，建议可以在`themes/<主题文件夹>/exampleSite/`中查看是否有相应的配置文件

#### 血的教训：

**不知道由于何种原因，如果主题文件夹中保留`.git`文件夹，vercel 部署时 99.9%会报错！也就是说，只有将主题文件夹中的所有文件都交由主项目进行 git 管理才可以！**

> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！
>
> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！
>
> 如果你是那 0.1%的幸运星，请**务必**告诉我你是怎么操作的！

### 使用模板创建项目

- github 上的模板有很多，直接搜索`hugo template`关键字就可以找到
- [这是我自己配置的一个模板](https://github.com/whosydd/hugo-even-template)，基于 Even 主题。只是进行了简单的配置，如果你的要求不高的话，可以直接使用该模板构建博客。只需要点击`Use this template`，设置好仓库名称，就可以根据模板创建自己的项目仓库了，之后只需要将创建好的仓库`clone`到本地，在项目根目录打开终端，使用`hugo new post/hello.md`命令就可以创建博文了。

## 配置选项

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
  # 如果设置为false，则不会在主页显示博文的内容预览
  showArchiveCount = true

  # 这是我新添加的选项，设置为true时，会在主页中的每篇博文中显示阅读更多
  # show 'read more' link ?
  readMore = false

  # 是否显示博文中的页脚信息（包含作者，上次修改时间，markdown链接，许可信息）
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

你可以在**[这里](https://favicon.io/favicon-generator/)**创建 favicon 图标，然后将解压之后的**所有图标文件**放到项目根目录的`static/`中即可

![Screenshot of Favicon Generator - Text to Favicon - favicon.io](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152248657.jpg)

### 博文模板

- 一般可以在`themes/<主题文件夹>/archetypes/`中找到博文模板，只需要将该文件复制一份，放到项目根目录中的`archetypes/`中即可。
- 建议只保留一些常用的配置项即可
- 其中的`Draft`配置项默认为`true`，表示该文章为草稿，发布时记得改为`false`
- 你可以在根目录的`content/post/`中查看所有的博文

## 推送到 github

### github 访问

[由于一些不可控因素，github 访问速度可能会很慢，此时你就会需要这个了](https://keylol.com/t256816-1-1)

### 创建远程仓库

1. 点击`+`选择`New repository`创建新仓库

![Screenshot of GitHub](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108152320408.jpg)

2. 给仓库起个名字，只能使用`-`连接符，例如：`hello-world`，其他默认

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

### 配置项目

![Screenshot of demo – Overview – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160100546.jpg)

#### 添加自定义域名

##### 注册域名

你可以在https://my.freenom.com/注册一个长达12个月的免费域名，不过这个网站大陆访问有点慢，不太推荐

##### 添加域名

1. 在此页面输入已注册的域名，会弹窗让你选择重定向，选择`Recommended`即可

![Screenshot of demo – Domains – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160105923.jpg)

2. 域名解析，这里建议直接选择 Nameservers，然后根据提示将`ns1.vercel-dns.com`和`ns2.vercel-dns.com`添加到注册域名网站的相关设置中即可

> 以https://my.freenom.com/注册的域名为例：注册成功后，需要在主页依次点击`Services -> My Domains -> Manage Domain -> Management Tools -> Nameservers`，选择`Use custom nameservers`，添加`ns1.vercel-dns.com`和`ns2.vercel-dns.com`即可

![Screenshot of demo – Domains – Vercel (2)](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160134606.jpg)

3. 修改`nameservers`后，点击`Refresh`刷新状态，如果都打钩了就可以了，此时就可以通过你填写的域名访问博客了

### 删除项目

`Settings -> Advanced -> Delete Project`

![Screenshot of demo – Advanced – Vercel](https://raw.githubusercontent.com/whosydd/images-in-one/main/202108160147843.jpg)

## 更新博客

### 新建文章

在项目根目录打开终端，使用`hugo new post/<文件名>.md`命令

### 推送到 github

在项目根目录打开终端，执行以下命令

```bash
# 添加所有文件到暂存区
git add .

# 提交commit
git commit -m 'updated'

# push到github
git push
```

### 自动部署

只要第一次部署成功后，以后只需要将本地新写的文章推送到 github 即可，vercel 会在每次 commit 后自动部署

## 最后

由于注册域名的网站打开实在是太慢了，所以域名注册相关我写的就比较简略，还望见谅~

## 最最后

如果发现有哪里写的不好或者不对的地方，欢迎 pr~

## 最最最后

希望通过这个教程，大家都能够搭建属于自己的博客~

## 最最最最后

**C'est la vie!**
