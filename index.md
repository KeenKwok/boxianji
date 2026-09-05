---
layout: default
title: 首页
---

# 拨弦记

> 以弦為引，聽見世界

---

![](images/weekly/cover.JPG)

## 弹拨乐一周简报

记录世界弹拨乐领域值得关注的艺术节、赛事、学术、乐器制作、非遗、演出及人物资讯。


{% assign weekly_posts = site.pages | where_exp: "page", "page.path contains 'weekly/'" | sort: "path" | reverse %}
{% assign latest_post = weekly_posts | first %}

### 最新一期

- [{{ latest_post.title }}]({{ site.baseurl }}{{ latest_post.url }})

### 往期简报

{% for post in weekly_posts offset:1 %}
{% if post.title and post.url %}
- [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endif %}
{% endfor %}

---

## 关于拨弦记

拨弦记，关注各地弹拨乐文化动态。
这里记录新闻，也记录音乐、人物、乐器与正在发生的现场。

<!--
---

* 拨弦记｜弹拨乐资讯、音乐分享与知识记录
-->
