---
layout: page
title: 涛神的乌托邦
tagline: Supporting tagline
---
{% include JB/setup %}
## About Me
![Pan Tao](http://pantaothu2-github.stor.sinaapp.com/images/header.jpg)

**Pan Tao**

Student of IE, Tsinghua University

I love technology and I love playing with technology.

That's all^-^
   
## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## Find Me elsewhere

[RenRen](http://www.renren.com/pantaovay/)
[Weibo](http://weibo.com/pantaovay/)

[Original WP Blog](http://www.godtao.tk/)

---

Power by [Markdown](http://daringfireball.net/projects/markdown/), [GitHub](https://github.com/), [Ruby](http://www.ruby-lang.org/en/), and [jekyll](https://github.com/mojombo/jekyll).