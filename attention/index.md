---
layout: default
title: 拨弦记｜演出情报
---

# 拨弦记｜演出情报

> 持续收录近期值得关注的弹拨乐演出，为现场音乐爱好者提供演出情报。

## 开放接口

<div style="
  border:1px solid #e5e5e5;
  border-radius:9px;
  padding:10px 13px;
  margin:10px 0;
  background:#fafafa;
">

  <div style="display:flex;align-items:center;justify-content:space-between;gap:12px;">

    <div style="display:flex;align-items:center;min-width:0;">
      <svg width="18" height="18" viewBox="0 0 24 24" style="margin-right:7px;flex-shrink:0;">
        <path fill="#F26522" d="M6.18 17.82A2.18 2.18 0 1 1 4 20a2.18 2.18 0 0 1 2.18-2.18z"/>
        <path fill="#F26522" d="M4 11.27v3.09A5.64 5.64 0 0 1 9.64 20h3.09A8.73 8.73 0 0 0 4 11.27z"/>
        <path fill="#F26522" d="M4 4v3.09A12.91 12.91 0 0 1 16.91 20H20A16 16 0 0 0 4 4z"/>
      </svg>

      <div style="min-width:0;">
        <strong style="font-size:0.95em;">演出情报 RSS</strong>
        <div style="font-size:0.76em;color:#888;margin-top:2px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;">
          attention.xml
        </div>
      </div>
    </div>

    <a href="https://keenkwok.github.io/boxianji/attention.xml"
       style="font-size:0.82em;white-space:nowrap;">
      打开 ↗
    </a>

  </div>

</div>

---

## 近期演出

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
