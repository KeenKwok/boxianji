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

- **🎫 {{ event.date | date: "%m.%d" }}｜{{ event.city }}｜{{ event.title }}**

{% endfor %}