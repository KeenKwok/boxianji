---
layout: default
title: 拨弦记｜演出情报
---

# 拨弦记｜演出情报

> 持续收录近期值得关注的弹拨乐演出，为现场音乐爱好者提供演出情报。

{% for event in site.data.attention %}
<div style="margin:1em 0;">
  <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
  <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small><br>
  {{ event.title }}
</div>
{% endfor %}

---

## 关于拨弦记

《拨弦记》持续关注世界弹拨乐领域的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

- 主理人网站：guitarkk.com
- GitHub：keenkwok.github.io/boxianji/
- 微信公众号：拨弦记
