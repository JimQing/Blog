---
layout: post
title:  "初建GitHub博客"
---

初建 github 博客，算是一段比较复杂的过程。
以下我来回顾一下我的过程

第一部分: Github Pages

首先你需要有个 [repository] 命名为 [你的博客名] 

并在此上传一个 html 文件到你的仓库 ( master 分支)

{% highlight code %}
#index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style type="text/css">
        h1{
            text-align: center;
            font-size: 50px;
        }
    </style>
</head>
<body>
    <h1>Hello Github</h1>   
</body>
</html>
{% endhighlight %}

进入你新建的博客中，选中菜单中的 Settings

![]({{ "../images\2019-03-17-settings.jpg" | absolute_url }})

接着下滑找到我们的GitHub Page，使其作为页面展示，选中master分支就好

![]({{ "../images\2019-03-17-page.jpg" | absolute_url }})

接着访问图中对应的链接 https://[用户名].github.io/[仓库名]]/

即可看到效果。

第二部分 安装 Jekll

想要安装 Jekll 需要安装 [Python][python] [Ruby][ruby] 以及 [nodeJs][nodejs].

安装完上述环境并置入环境变量后，检查 ruby

{% highlight ruby %}
ruby -v
# 对应版本号
gem -v
# 对应版本号
{% endhighlight %}

由于 gem 在大陆使用是会被墙的，如果没有科学上网，可以选择镜像

{% highlight ruby %}
gem sources
#查看源
gem sources -r https://rubygems.org/
#删除默认源
gem sources -a https://gems.ruby-china.com
#更换为镜像源
gem sources -u
#更新源的缓存
{% endhighlight %}

如果显示正常，我们就完成了对应的环境安装，安装 [Jekyll][Jekyll]

{% highlight ruby %}
gem install jekyll
{% endhighlight %}

接着我们去 [jekyllthemes][themes] 选一个喜欢的主题

并下载解压到你的 [repository] 目录下，通过 gem 安装 bundle

{% highlight ruby %}
gem install bundle
#安装 bundle
bundle -v
#对应版本号
bundle install
#安装依赖
bundle exec jekyll serve -w
#运行!!
#-w 表示实时检查改动，可以边书写博客一边查看效果
{% endhighlight %}

运行成功即可在 http://127.0.0.1:4000/ 查看效果

Tips: 

1. 在更换源之后如果依旧下载异常，检查下载主题目录下是否有 Gemfile 文件，更换其中的source 即可

{% highlight ruby %}
# A sample Gemfile
source "http://gems.ruby-china.com/"
gemspec

gem 'jekyll'
gem 'jekyll-paginate'
gem 'kramdown'
gem 'pygments.rb'
{% endhighlight %}

2. 在执行 install 的时候需要检查你的主题的文件 jekyll-[主题名]-theme.gemspec 对应的版本是否与你的安装版本相同，否则会 install 报错

{% highlight ruby %}
spec.add_development_dependency "jekyll", "~> 3.2"
spec.add_development_dependency "bundler", "2.0.1"
spec.add_development_dependency "rake", "~> 10.0"
{% endhighlight %}

[python]:    https://www.python.org/
[ruby]:      http://www.ruby-lang.org/en/documentation/installation/
[nodejs]:    http://nodejs.cn/
[Jekyll]:    http://Jekyllrb.com
[themes]:    http://jekyllthemes.org/