---
layout: default
title: 首页
---

# 拨弦记

> 记录弹拨乐，发现弦上世界。

---

![](images/weekly/cover.JPG)

## 弹拨乐一周简报

记录世界弹拨乐领域值得关注的艺术节、赛事、学术、乐器制作、非遗、演出及人物资讯。

### 最新一期

{% assign weekly_posts = site.pages | where_exp: "page", "page.path contains 'weekly/'" | sort: "path" | reverse %}

{% for post in weekly_posts %}
- [{{ post.title }}]({{ site.baseurl }}/{{ post.path }})
{% endfor %}

---

## 关于撥弦記

撥弦記，关注古典吉他、中国民族弹拨乐器及世界各地弹拨乐文化。

这里记录新闻，也记录音乐、人物、乐器与正在发生的现场。

---

*撥弦記｜记录弦上世界*