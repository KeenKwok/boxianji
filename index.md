---
layout: default
title: 首页
---

# 拨弦记

> 记录弹拨乐，发现弦上世界。

---

## 演出情报

《拨弦记》持续更新弹拨乐近期重要演出。

{% for event in site.data.attention limit:3 %}
<div style="margin:0.9em 0;">
  <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
  <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small><br>
  {{ event.title }}
</div>
{% endfor %}

→ [查看全部演出情报](attention/)

---

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

## 开放接口

<span style="font-size:0.82em;color:#777;">
  演出情报开放数据：
</span>

<span style="white-space:nowrap;">
  <svg width="15" height="15" viewBox="0 0 24 24" style="vertical-align:-2px;margin-right:3px;">
    <path fill="#F26522" d="M6.18 17.82A2.18 2.18 0 1 1 4 20a2.18 2.18 0 0 1 2.18-2.18z"/>
    <path fill="#F26522" d="M4 11.27v3.09A5.64 5.64 0 0 1 9.64 20h3.09A8.73 8.73 0 0 0 4 11.27z"/>
    <path fill="#F26522" d="M4 4v3.09A12.91 12.91 0 0 1 16.91 20H20A16 16 0 0 0 4 4z"/>
  </svg>
  <a href="attention.xml">RSS 订阅</a>
</span>

&nbsp;·&nbsp;

<span style="white-space:nowrap;">
  <span style="
    display:inline-block;
    font-family:monospace;
    font-size:12px;
    font-weight:bold;
    color:#555;
    margin-right:3px;
  ">{ }</span>
  <a href="attention.json">JSON 数据</a>
</span>

---

## 关于拨弦记

《拨弦记》持续关注世界弹拨乐领域的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

- 主理人网站：guitarkk.com
- GitHub：keenkwok.github.io/boxianji/
- 微信公众号：拨弦记
