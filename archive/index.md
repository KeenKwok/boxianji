---
layout: default
title: 演出档案
---

# 演出档案

{% assign events = site.data.attention | sort: "date" | reverse %}

{% assign current_year = "" %}
{% assign current_month = "" %}

{% for event in events %}

  {% assign event_year = event.date | date: "%Y" %}
  {% assign event_month = event.date | date: "%m" %}

  {% if event_year != current_year %}
    {% assign current_year = event_year %}
    {% assign current_month = "" %}

## {{ current_year }}

  {% endif %}

  {% if event_month != current_month %}
    {% assign current_month = event_month %}

### {{ current_month | plus: 0 }}月

  {% endif %}

<div style="margin:0.75em 0;">
  <div style="line-height:1.35;margin-bottom:2px;">
    <strong>🎫 {{ event.date | date: "%m.%d" }}｜{{ event.city }}</strong>
    <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small>
  </div>

  <div style="line-height:1.35;font-weight:600;">
    {{ event.title }}
  </div>

  {% if event.performers and event.performers.size > 0 %}
  <div style="margin-top:1px;font-size:0.78em;line-height:1.25;color:#777;">
    演奏者：{{ event.performers | join: " · " }}
  </div>
  {% endif %}

  {% if event.instruments and event.instruments.size > 0 %}
  <div style="margin-top:0;font-size:0.78em;line-height:1.25;color:#777;">
    乐器：{{ event.instruments | join: " · " }}
  </div>
  {% endif %}
</div>

{% endfor %}