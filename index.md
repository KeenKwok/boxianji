---
layout: default
title: 首页
---

# 拨弦记

> 记录弹拨乐，发现弦上世界。

---

## 演出情报

未来14天值得关注的弹拨乐演出。

{% assign today = site.time | date: "%s" %}
{% assign fourteen_days = 1209600 %}
{% assign has_recent = false %}

{% for event in site.data.attention %}
  {% assign event_time = event.date | date: "%s" %}
  {% assign diff = event_time | minus: today %}

  {% if diff >= 0 and diff <= fourteen_days %}
    {% assign has_recent = true %}

<div style="margin:0.75em 0;">

  <div style="
    line-height:1.35;
    margin-bottom:2px;
  ">
    <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
    <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small>
  </div>

  <div style="
    line-height:1.35;
    font-weight:600;
  ">
    {{ event.title }}
  </div>

  {% if event.performers and event.performers.size > 0 %}
  <div style="
    margin-top:1px;
    font-size:0.78em;
    line-height:1.25;
    color:#777;
  ">
    演奏者：{{ event.performers | join: " · " }}
  </div>
  {% endif %}

  {% if event.instruments and event.instruments.size > 0 %}
  <div style="
    margin-top:0;
    font-size:0.78em;
    line-height:1.25;
    color:#777;
  ">
    乐器：{{ event.instruments | join: " · " }}
  </div>
  {% endif %}

</div>

  {% endif %}
{% endfor %}

{% unless has_recent %}
> 未来14天暂无收录演出。
{% endunless %}

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

<h2>开放接口</h2>

<p style="font-size:0.82em;color:#777;margin-top:-6px;">
  演出情报开放数据：
</p>

<p style="margin-top:-4px;">
  <a href="{{ site.baseurl }}/attention.xml">
    <span style="color:#F26522;">◉</span> RSS 订阅
  </a>
  &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/attention.json">
    <span style="font-family:monospace;font-weight:bold;color:#555;">{ }</span> JSON 数据
  </a>
</p>