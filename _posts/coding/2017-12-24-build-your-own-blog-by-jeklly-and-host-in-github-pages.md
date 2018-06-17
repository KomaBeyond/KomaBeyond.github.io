---
title: Build your own blog bu Jekyll and host in github pages
permalink: /coding/build-blog-by-jekyll
---

## 基于 github pages 使用 Jekyll 构建个人博客

> #### **Step1 创建 github pages 仓库**

这里请直接参考 github pages [引导](https://pages.github.com/)，按规则建好仓库之后将其 clone 到本地，后面我们会用到它。**注意：** 使用 master 分支


> #### **Step2 安装 Ruby**

Jekyll 的运行是基于 Ruby 来的，因此我们需要先安装它，后续本地博客环境的启动也是基于 Ruby 的。
这里要求 Ruby 的版本在 2.2.5 以上，因此最好采用源码安装方式，由于我的系统是 Ubuntu 所以源码安装相对简单，具体安装可参考[这里](https://www.ruby-lang.org/zh_cn/documentation/installation/)


> #### **Step3 安装 Jekyll 和 Bundle**

Ruby 组件 Jekyll 可以用来快速创建基于 Jekyll 的博客系统，稍后我们会使用 Jekyll 工具建立一个示例博客来初始化我们的博客系统。Bundle 工具则是用来启动本地博客环境，这样方便本地调试。

首先请参考 Jekyll 的 [Quick start](https://jekyllrb.com/docs/quickstart/) 创建一个简单示例博客并通过 Bundle 启动，然后在浏览器中测试成功。这里需要记住一条命令，如下：
```bash
bundle exec jekyll serve
```

> #### **Step4 修改 Gemfile并部署到 github pages**

在示例博客的目录下找到 Gemfile 文件，打开并将以下代码注释掉
```bash
gem "jekyll", "~> 3.6.2"
```
然后将下面的代码反注释
```bash
# gem "github-pages", group: :jekyll_plugins
```
执行完上述操作之后，将示例代码的全部文件拷贝到我们之前 clone 下来的 github pages 仓库，并在 master 分支上提交并推送到远端，然后在浏览器中访问： *http://username.github.io* 如果没问题的话则能够看到我们的示例博客内容，这就表示我们的博客到此就已经搭建成功了。

> #### **Step5 修改博客主题**

首先在[这里](https://pages.github.com/themes/)查看 githb pages 所支持的所有主题，然后选择一个你中意的，这里我选择了 minimal。

然后修改 Gemfile 里的代码
```bash
gem "minima", "~> 2.0"
```
为
```bash
gem "minimal"
```
修改 \_config.yml 里的 theme 配置为
```bash
theme: jekyll-theme-minimal
```

接着执行如下两条命令来安装主题及更新对应的依赖库
```bash
bundle install
bundle update
```
然后将 minimal 主题里的 index.md 文件拷贝到我们的示例博客下，然后运行命令
```bash
bundle exec jekyll serve
```
启动本地环境，通过浏览器访问 http://127.0.0.1:4000 访问去查看主题效果，如果正常，则表示我们的主题更换成功，接下来就是根据该主题做一下个人的自定义，那么以后我们就可以依据该主题编写我们的博客啦。

> #### **Step6 说在最后**

执行完成上述所有步骤之后，将代码推送到 github 之后我们就能够通过 github pages 的域名访问到我们的博客啦，后续关于个人自定义的操作因人而异，如果你实在不知道该如何开始的话可以参考我这个博客的初始环境，你可以在[这里](https://github.com/KomaBeyond/komabeyond.github.io/releases)下载到这个博客的初始环境，它只是接着上述的第五步之后做了一些简单自定义。
