---
layout: default
title: 近期值得关注
---

# 近期值得关注

> 汇总近期值得关注的弹拨乐音乐会、艺术节、大师班及巡演资讯。

{% for event in site.data.attention %}
<div style="margin:1.1em 0;">
<strong>🎫 {{ event.date }}｜{{ event.city }}</strong><br>
{{ event.title }}<br>
<small><a href="{{ event.link }}">查看演出海报（公众号）↗</a></small>
</div>
{% endfor %}
