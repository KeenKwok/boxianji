---
layout: default
title: 演出档案
---

# 演出档案

{% assign events = site.data.attention | sort: "date" | reverse %}

{% assign current_year = "" %}

{% for event in events %}

  {% assign event_year = event.date | date: "%Y" %}

  {% if event_year != current_year %}
    {% assign current_year = event_year %}

## {{ current_year }}

  {% endif %}

- **🎫 {{ event.date | date: "%m.%d" }}｜{{ event.city }}｜{{ event.title }}**

{% endfor %}