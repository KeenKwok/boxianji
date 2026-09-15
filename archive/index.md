---
layout: default
title: 演出档案
---

# 演出档案

{% assign events = site.data.attention | sort: "date" | reverse %}

{% assign current_year = "" %}
{% assign current_month = "" %}
{% assign month_events = "" %}

{% for event in events %}

  {% assign event_year = event.date | date: "%Y" %}
  {% assign event_month = event.date | date: "%m" %}

  {% if event_year != current_year %}
    {% assign current_year = event_year %}
    {% assign current_month = "" %}
  {% endif %}

  {% if event_month != current_month %}

    {% if current_month != "" %}
      <div style="margin-top:-0.8em;margin-bottom:1.2em;font-size:0.78em;color:#999;">
        共 {{ month_events.size }} 场
      </div>
    {% endif %}

    {% assign current_month = event_month %}
    {% assign month_events = "" | split: "" %}

    {% for month_event in events %}
      {% assign month_event_year = month_event.date | date: "%Y" %}
      {% assign month_event_month = month_event.date | date: "%m" %}

      {% if month_event_year == current_year and month_event_month == current_month %}
        {% assign month_events = month_events | push: month_event %}
      {% endif %}
    {% endfor %}

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

{% if current_month != "" %}
  <div style="margin-top:-0.8em;margin-bottom:1.2em;font-size:0.78em;color:#999;">
    共 {{ month_events.size }} 场
  </div>
{% endif %}