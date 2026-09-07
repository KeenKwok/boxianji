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

### 最新一期

{% for post in weekly_posts limit:4 %}
  {% unless post.path == "weekly/index.md" %}
- [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
    {% break %}
  {% endunless %}
{% endfor %}

### 往期简报

{% assign latest_found = false %}

{% for post in weekly_posts %}
  {% unless post.path == "weekly/index.md" %}
    {% if latest_found %}
- [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
    {% else %}
      {% assign latest_found = true %}
    {% endif %}
  {% endunless %}
{% endfor %}

→ [查看全部周报](weekly/)

---

## 演出情报

{% for event in site.data.attention limit:3 %}
<div style="margin:0.9em 0;">
  <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
  <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small><br>
  {{ event.title }}
</div>
{% endfor %}

→ [查看全部演出情报](attention/)

---

## 关于拨弦记

《拨弦记》持续关注世界弹拨乐领域的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

- 主理人网站：guitarkk.com
- GitHub：keenkwok.github.io/boxianji/
- 微信公众号：拨弦记

<!--
---

* 拨弦记｜弹拨乐资讯、音乐分享与知识记录
-->
