---
layout: default
title: 拨弦记｜周报归档
exclude_from_weekly: true
---

# 拨弦记｜周报归档

> 收录《拨弦记》历期《弹拨乐一周简报》，持续记录世界弹拨乐领域的重要资讯。

{% assign reports = site.pages | where_exp:"p","p.path contains 'weekly/'" | sort:"path" | reverse %}

{% for report in reports %}
{% unless report.path == "weekly/index.md" %}

<div style="
  margin:0.85em 0;
  line-height:1.35;
">

  <div>
    <strong>{{ report.title }}</strong>
  </div>

  <div style="
    margin-top:1px;
    font-size:0.78em;
    line-height:1.25;
  ">
    <a href="{{ site.baseurl }}{{ report.url }}">阅读全文 ↗</a>
  </div>

</div>

{% endunless %}
{% endfor %}