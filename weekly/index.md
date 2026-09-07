---
layout: default
title: 拨弦记|周报归档
exclude_from_weekly: true
---

# 拨弦记|周报归档

> 收录《拨弦记》历期《弹拨乐一周简报》，持续记录世界弹拨乐领域的重要资讯。

{% assign reports = site.pages | where_exp:"p","p.path contains 'weekly/'" | sort:"path" | reverse %}

{% for report in reports %}
{% unless report.path == "weekly/index.md" %}
<div style="margin:1em 0;">
  <strong>{{ report.title }}</strong><br>
  <small><a href="{{ site.baseurl }}{{ report.url }}">阅读全文 ↗</a></small>
</div>
{% endunless %}
{% endfor %}

---

## 关于拨弦记

《拨弦记》持续关注世界弹拨乐领域的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

- 主理人网站：guitarkk.com
- GitHub：keenkwok.github.io/boxianji/
- 微信公众号：拨弦记
