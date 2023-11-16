[Zqq Blog](https://zhnagqqf.me)
================================

> I never expect this becomes popular. -- Hux


![](http://huangxuan.me/img/blog-desktop.jpg)


[User Manual 👉](_doc/Manual.md)
--------------------------------------------------

## Usage
将[Hux](https://github.com/Huxpro/huxpro.github.io)的仓库clone下来后，本地的jekyll还需`install jekyll-paginate`，并在Gemfile文件中添加`gem 'jekyll-paginate'`语句方可使用

### Audio
在左上角添加背景音乐，首先在[nav.html](_includes/nav.html)中注释掉原来的超链接
```
<a class="navbar-brand" href="{{ site.baseurl }}/">{{ site.title }}</a>
```
再用object插入audio。

### Comments
github pages本身没有评论系统，需要借助第三方评论系统。

**[disqus](https://disqus.com/)**

[Hux Blog](http://huangxuan.me)使用的评论系统，但国内无法访问

**gitalk**

基于github的评论系统，也是[BY](https://qiubaiying.github.io/)使用的评论系统，只有github用户方可评论。

用法：

- 注册一个[application](https://github.com/settings/applications/new)，Authorization callback URL写博客地址，Homepage URL好像写博客地址或仓库地址都行。
- 获取Client ID和Client secret。
- 勾选博客仓库的issues，评论就是issues
- 在_config.yml填写信息：
    ```yml
    gitalk:
        enable: true                                              #是否开启Gitalk评论
        clientID: ef4b7ef11cb3c459144b                            #生成的clientID
        clientSecret: c9f776259af51fb0c95414ae8cd72c90f46dfc6d    #生成的clientSecret
        repo: zhangqqf.github.io                                  #仓库名称
        owner: zhangqqf                                           #github用户名
        admin: zhangqqf
        distractionFreeMode: true                                 #是否启用类似FB的阴影遮罩
    ```
- 在ABOUT界面插入评论系统
    - 在about.html文件中插入：
        ```html
        <!-- Gitalk 评论 start  -->
        {% if site.gitalk.enable %}
        <!-- Gitalk link  -->
        <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
        <script src="https://unpkg.com/gitalk@latest/dist/gitalk.min.js"></script>

        <div id="gitalk-container"></div>
            <script type="text/javascript">
            var gitalk = new Gitalk({
            clientID: '{{site.gitalk.clientID}}',
            clientSecret: '{{site.gitalk.clientSecret}}',
            repo: '{{site.gitalk.repo}}',
            owner: '{{site.gitalk.owner}}',
            admin: ['{{site.gitalk.admin}}'],
            distractionFreeMode: {{site.gitalk.distractionFreeMode}},
            // id: 'about',
            id: window.location.pathname,
            title: 'comments',
            language:'en',
            });
            gitalk.render('gitalk-container');
        </script>
        {% endif %}
        <!-- Gitalk 评论 end  -->
        ```
- 在每篇博客下面插入评论系统
    - 在post.html文件插入上述与about一样的内容即可

几个问题：

- 关于Error: Validation Failed的解决，倾向于增加title属性，而非什么字段太长，title的值随便给都行
- id随便给也行

**[LiveRe 来必力](https://www.livere.com/)**

韩国的第三方评论系统，支持国内外一大堆社交工具登录评论，配置简单，注册个[LiveRe 来必力](https://www.livere.com/)账号然后把代码直接复制到about.html和post.html就可以了。



### Analytics
Google需要梯子，用[百度统计](https://tongji.baidu.com/web/welcome/login)


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
