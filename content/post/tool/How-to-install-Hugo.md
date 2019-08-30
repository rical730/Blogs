---
title: "如何像本博客一样搭建github.io"
date: 2019-08-30
categories:
- 工具
tags:
- github
keywords:
- github.io
- hugo
showSocial: false
autoThumbnailImage: false
thumbnailImagePosition: "top"
thumbnailImage: //d1u9biwaxjngwg.cloudfront.net/welcome-to-tranquilpeak/city-750.jpg
coverImage: //d1u9biwaxjngwg.cloudfront.net/welcome-to-tranquilpeak/city.jpg
metaAlignment: center
---
从开始写博客到现在，CSDN和简书都试过，但还是想建立一个自己的博客网站，可是又嫌维护服务器麻烦，github.io简直是完美选择，没想到还可以个性化定制主题，于是果断种草。
<!--more-->
<!-- toc -->


# 准备工作
<!--[![Join the chat at https://gitter.im/LouisBarranqueiro/hexo-theme-tranquilpeak](https://badges.gitter.im/Join%20Chat.svg)](http s://gitter.im/LouisBarranqueiro/hexo-theme-tranquilpeak?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)-->

- 拥有一个自己的GitHub账号。[[GitHub地址](https://github.com)]
- 创建一个名为`<yourusername>.github.io`的仓库。[[参考博客](https://blog.csdn.net/Tang_Chuanlin/article/details/83626545): 不需要配置github默认的主题]
- 创建一个名为`blogs`的仓库：准备存放hugo生成的静态网站数据。

> 本博客参考[如何在github.io搭建Hugo博客站](https://keysaim.github.io/post/blog/deploy-hugo-blog-in-github.io/)


# 搭建Hogo博客

- **Step1: 安装Hugo**: (在mac上运行)
```sh
brew install hugo
```

- **Step2: 在本地建站并关联自己存放博客文件的仓库**：`blogs`就是自己建的那个仓库
```sh
hugo new site blogs
cd blogs
git init
git remote add origin git@github.com:rical730/blogs.git
```

- **Step3: 添加一个Hugo主题**
    - Hugo官方有非常多免费开源的主题，[快去挑选一下](https://themes.gohugo.io/)
    - 本文选用的主题：[tranquilpeak](https://themes.gohugo.io/hugo-tranquilpeak-theme/)
    - 推荐几个我喜欢的其他主题
        - 写书专用：[techdoc](https://themes.gohugo.io/hugo-theme-techdoc/)
        - 简历专用：[resume](https://themes.gohugo.io/hugo-resume/)
        - 码农专用：[nix](https://themes.gohugo.io/hugo-theme-nix/)
    - 添加方式
```sh
git submodule add -b master https://github.com/kakawait/hugo-tranquilpeak-theme.git themes/hugo-tranquilpeak-theme
```
    - 拷贝模板 
```sh
cp -r themes/hugo-tranquilpeak-theme/exampleSite/* ./
```

- **Step4: 本地测试**: 在根目录下
```sh
hugo server
```
然后本地浏览器打开：`http://localhost:1313`，就可以开始改造你的博客了。

如果想热编辑（就是修改后Ctrl+s可以直接看博客效果的话，可使用
```sh
hugo server --disableFastRender
```

# 修改默认配置
`Hugo`默认配置文件是`config.toml`，配置都比较显而易见，有几个重要配置可以改一下。

1. 修改`baseURL`: 改成你的博客最终部署的url，比如`https://rical730.github.io/`
2. 修改`paginate`: 首页每页博文数量显示 
3. 修改`languageCode`: 如果网站要显示成中文，要修改为`zh-cn`

# 编辑博文&&提交修改
- 默认情况下，博文放在content/post/下面，可以新建目录编辑
- 编写完成后，本地查看下没什么问题，先提交到管理博客的仓库`blogs`里：
```
git add ./*
git commit -m "YOUR COMMIT MESSAGE"
git push origin master
```
 > 如果有账号权限问题，说明之前没有配置ssh，可以参考[这篇博客](https://www.awaimai.com/2200.html)配置


