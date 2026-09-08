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

<div style="
  border:1px solid #e5e5e5;
  border-radius:12px;
  padding:16px 18px;
  margin:16px 0;
  background:#fafafa;
">

  <div style="display:flex;align-items:center;margin-bottom:8px;">
    <svg width="22" height="22" viewBox="0 0 24 24" style="margin-right:9px;flex-shrink:0;">
      <path fill="#F26522" d="M6.18 17.82A2.18 2.18 0 1 1 4 20a2.18 2.18 0 0 1 2.18-2.18z"/>
      <path fill="#F26522" d="M4 11.27v3.09A5.64 5.64 0 0 1 9.64 20h3.09A8.73 8.73 0 0 0 4 11.27z"/>
      <path fill="#F26522" d="M4 4v3.09A12.91 12.91 0 0 1 16.91 20H20A16 16 0 0 0 4 4z"/>
    </svg>

    <strong style="font-size:1.05em;">
      演出情报 RSS
    </strong>
  </div>

  <div style="font-size:0.9em;color:#666;margin-bottom:10px;">
    订阅《拨弦记》近期演出情报
  </div>

  <div style="
    background:#fff;
    border:1px solid #eee;
    border-radius:7px;
    padding:8px 10px;
    font-size:0.82em;
    overflow-wrap:anywhere;
  ">
    https://keenkwok.github.io/boxianji/attention.xml
  </div>

  <div style="margin-top:10px;">
    <a href="https://keenkwok.github.io/boxianji/attention.xml">
      打开 RSS ↗
    </a>
  </div>

</div>

---

## 关于拨弦记

《拨弦记》持续关注世界弹拨乐领域的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

- 主理人网站：guitarkk.com
- GitHub：keenkwok.github.io/boxianji/
- 微信公众号：拨弦记
