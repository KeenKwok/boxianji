---
layout: default
title: 拨弦记｜演出情报
---

# 拨弦记｜演出情报

> 持续收录近期值得关注的弹拨乐演出，为现场音乐爱好者提供演出情报。

<div style="margin:18px 0 10px;">
  <div style="
    font-size:1.05em;
    font-weight:600;
    letter-spacing:0.02em;
    line-height:1.3;
  ">
    开放接口
  </div>

  <div style="
    margin-top:2px;
    font-size:0.72em;
    color:#999;
    letter-spacing:0.04em;
  ">
    Open Feeds &amp; Data
  </div>
</div>

<div style="
  border:1px solid #e5e5e5;
  border-radius:8px;
  padding:8px 11px;
  margin:8px 0;
  background:#fafafa;
">

  <div style="display:flex;align-items:center;margin-bottom:2px;">
    <svg width="18" height="18" viewBox="0 0 24 24" style="margin-right:6px;flex-shrink:0;">
      <path fill="#F26522" d="M6.18 17.82A2.18 2.18 0 1 1 4 20a2.18 2.18 0 0 1 2.18-2.18z"/>
      <path fill="#F26522" d="M4 11.27v3.09A5.64 5.64 0 0 1 9.64 20h3.09A8.73 8.73 0 0 0 4 11.27z"/>
      <path fill="#F26522" d="M4 4v3.09A12.91 12.91 0 0 1 16.91 20H20A16 16 0 0 0 4 4z"/>
    </svg>

    <strong style="font-size:0.92em;">
      演出情报 RSS
    </strong>
  </div>

  <div style="font-size:0.78em;color:#777;margin-bottom:4px;">
    订阅《拨弦记》近期演出情报
  </div>

  <div style="
    background:#fff;
    border:1px solid #eee;
    border-radius:5px;
    padding:4px 7px;
    font-size:0.72em;
    line-height:1.25;
    overflow-wrap:anywhere;
  ">
    https://keenkwok.github.io/boxianji/attention.xml
  </div>

  <div style="margin-top:4px;font-size:0.8em;line-height:1.2;">
    <a href="https://keenkwok.github.io/boxianji/attention.xml">
      打开 RSS ↗
    </a>
  </div>

</div>

<div style="
  border:1px solid #e5e5e5;
  border-radius:8px;
  padding:8px 11px;
  margin:8px 0;
  background:#fafafa;
">

  <div style="display:flex;align-items:center;margin-bottom:2px;">
    <span style="
      width:18px;
      height:18px;
      margin-right:6px;
      flex-shrink:0;
      display:inline-flex;
      align-items:center;
      justify-content:center;
      font-family:monospace;
      font-size:13px;
      font-weight:bold;
      color:#555;
      white-space:nowrap;
    ">
      { }
    </span>

    <strong style="font-size:0.92em;">
      演出情报 JSON
    </strong>
  </div>

  <div style="font-size:0.78em;color:#777;margin-bottom:4px;">
    获取《拨弦记》结构化演出数据
  </div>

  <div style="
    background:#fff;
    border:1px solid #eee;
    border-radius:5px;
    padding:4px 7px;
    font-size:0.72em;
    line-height:1.25;
    overflow-wrap:anywhere;
  ">
    https://keenkwok.github.io/boxianji/attention.json
  </div>

  <div style="margin-top:4px;font-size:0.8em;line-height:1.2;">
    <a href="https://keenkwok.github.io/boxianji/attention.json">
      打开 JSON ↗
    </a>
  </div>

</div>

---

## 近期演出

{% assign today = site.time | date: "%Y-%m-%d" %}

{% for event in site.data.attention %}
  {% if event.date >= today %}
<div style="margin:1em 0;">
  <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
  <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small><br>
  {{ event.title }}
</div>
  {% endif %}
{% endfor %}

{% assign has_past = false %}

{% for event in site.data.attention %}
  {% if event.date < today %}
    {% assign has_past = true %}
  {% endif %}
{% endfor %}

{% if has_past %}

<hr>

## 已结束

{% for event in site.data.attention %}
  {% if event.date < today %}
<div style="
  margin:0.8em 0;
  color:#888;
">
  <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
  <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small><br>
  {{ event.title }}
</div>
  {% endif %}
{% endfor %}

{% endif %}