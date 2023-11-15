[Zqq Blog](https://zhnagqqf.me)
================================

> I never expect this becomes popular. -- Hux

> “夫唯不争，故天下莫能与之争” -- Zqq

![](http://huangxuan.me/img/blog-desktop.jpg)


[User Manual 👉](_doc/Manual.md)
--------------------------------------------------

## Usage
-----
将Hux的仓库clone下来后，本地的jekyll还需`install jekyll-paginate`，并在Gemfile文件中添加`gem 'jekyll-paginate'`语句方可使用

### Audio
在左上角添加背景音乐，首先在[nav.html](_includes/nav.html)中注释掉原来的超链接
```
<a class="navbar-brand" href="{{ site.baseurl }}/">{{ site.title }}</a>
```
再用object插入audio。

### Comments
因[disqus](https://disqus.com/)需要梯子，因此借鉴[BY](https://github.com/qiubaiying/qiubaiying.github.io)用gitalk。


License
-------

>Zqq

Fork from [Hux](https://github.com/Huxpro/huxpro.github.io)

And Don't forget [BY](https://github.com/qiubaiying/qiubaiying.github.io), just through her to found Hux


>Hux

Apache License 2.0.
Copyright (c) 2015-present Huxpro

Hux Blog is derived from [Clean Blog Jekyll Theme (MIT License)](https://github.com/BlackrockDigital/startbootstrap-clean-blog-jekyll/)
Copyright (c) 2013-2016 Blackrock Digital LLC.
