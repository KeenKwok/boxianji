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
    订阅《拨弦记》近期演出情报 <a href="{{ site.url }}{{ site.baseurl }}/attention.xml">
      打开 RSS ↗</a>
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
    {{ site.url }}{{ site.baseurl }}/attention.xml
  </div>

<!--
  <div style="margin-top:4px;font-size:0.8em;line-height:1.2;">
    <a href="{{ site.url }}{{ site.baseurl }}/attention.xml">
      打开 RSS ↗
    </a>
  </div>
-->

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
    获取《拨弦记》结构化演出数据 <a href="{{ site.url }}{{ site.baseurl }}/attention.json">
      打开 JSON ↗
    </a>
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
    {{ site.url }}{{ site.baseurl }}/attention.json
  </div>

<!--
  <div style="margin-top:4px;font-size:0.8em;line-height:1.2;">
    <a href="{{ site.url }}{{ site.baseurl }}/attention.json">
      打开 JSON ↗
    </a>
  </div>
-->

</div>

---

## 近期演出

<div id="city-filter" style="
  display:flex;
  flex-wrap:wrap;
  gap:6px;
  margin:10px 0 16px;
">

  <button
    type="button"
    data-city-filter="全部"
    style="
      border:1px solid #ddd;
      border-radius:16px;
      padding:5px 11px;
      background:#222;
      color:#fff;
      font-size:0.78em;
      line-height:1.2;
      cursor:pointer;
    "
  >
    全部
  </button>

</div>

{% assign today = site.time | date: "%Y-%m-%d" %}

<div id="upcoming-events">

{% for event in site.data.attention %}
  {% if event.date >= today %}

<div
  class="event-item"
  data-city="{{ event.city | escape }}"
  style="margin:0.75em 0;"
>

  <div style="
    line-height:1.35;
    margin-bottom:2px;
  ">
    <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
    <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small>
  </div>

  <div style="
    line-height:1.35;
    font-weight:600;
  ">
    {{ event.title }}
  </div>

  {% if event.performers and event.performers.size > 0 %}
  <div style="
    margin-top:1px;
    font-size:0.78em;
    line-height:1.25;
    color:#777;
  ">
    演奏者：{{ event.performers | join: " · " }}
  </div>
  {% endif %}

  {% if event.instruments and event.instruments.size > 0 %}
  <div style="
    margin-top:0;
    font-size:0.78em;
    line-height:1.25;
    color:#777;
  ">
    乐器：{{ event.instruments | join: " · " }}
  </div>
  {% endif %}

</div>

  {% endif %}
{% endfor %}

</div>


{% assign has_past = false %}

{% for event in site.data.attention %}
  {% if event.date < today %}
    {% assign has_past = true %}
  {% endif %}
{% endfor %}


{% if has_past %}

<div id="past-events-section">

<hr>

## 已结束

<div id="past-events">

{% for event in site.data.attention %}
  {% if event.date < today %}

<div
  class="event-item"
  data-city="{{ event.city | escape }}"
  style="
    margin:0.65em 0;
    color:#888;
  "
>

  <div style="
    line-height:1.35;
    margin-bottom:2px;
  ">
    <strong>🎫 {{ event.date }}｜{{ event.city }}</strong>
    <small>｜<a href="{{ event.link }}">查看详情 ↗</a></small>
  </div>

  <div style="
    line-height:1.35;
    font-weight:600;
  ">
    {{ event.title }}
  </div>

  {% if event.performers and event.performers.size > 0 %}
  <div style="
    margin-top:1px;
    font-size:0.78em;
    line-height:1.25;
    color:#999;
  ">
    演奏者：{{ event.performers | join: " · " }}
  </div>
  {% endif %}

  {% if event.instruments and event.instruments.size > 0 %}
  <div style="
    margin-top:0;
    font-size:0.78em;
    line-height:1.25;
    color:#999;
  ">
    乐器：{{ event.instruments | join: " · " }}
  </div>
  {% endif %}

</div>

  {% endif %}
{% endfor %}

</div>
</div>

{% endif %}


<script>
(function () {
  var filterBox = document.getElementById('city-filter');

  if (!filterBox) return;

  var events = document.querySelectorAll('.event-item');
  var cities = [];

  events.forEach(function (event) {
    var city = event.getAttribute('data-city');

    if (city && cities.indexOf(city) === -1) {
      cities.push(city);
    }
  });

  cities.sort(function (a, b) {
    return a.localeCompare(b, 'zh-CN');
  });

  cities.forEach(function (city) {
    var button = document.createElement('button');

    button.type = 'button';
    button.textContent = city;
    button.setAttribute('data-city-filter', city);

    button.style.cssText = `
      border:1px solid #ddd;
      border-radius:16px;
      padding:5px 11px;
      background:#fff;
      color:#555;
      font-size:0.78em;
      line-height:1.2;
      cursor:pointer;
    `;

    filterBox.appendChild(button);
  });

  var buttons = filterBox.querySelectorAll('button');
  var pastSection = document.getElementById('past-events-section');

  function applyFilter(city) {

    events.forEach(function (event) {
      var eventCity = event.getAttribute('data-city');

      if (city === '全部' || eventCity === city) {
        event.style.display = '';
      } else {
        event.style.display = 'none';
      }
    });

    buttons.forEach(function (button) {
      var isActive = button.getAttribute('data-city-filter') === city;

      button.style.background = isActive ? '#222' : '#fff';
      button.style.color = isActive ? '#fff' : '#555';
      button.style.borderColor = isActive ? '#222' : '#ddd';
    });

    if (pastSection) {
      var pastEvents = pastSection.querySelectorAll('.event-item');
      var hasVisiblePastEvent = false;

      pastEvents.forEach(function (event) {
        if (event.style.display !== 'none') {
          hasVisiblePastEvent = true;
        }
      });

      pastSection.style.display = hasVisiblePastEvent ? '' : 'none';
    }
  }

  buttons.forEach(function (button) {
    button.addEventListener('click', function () {
      applyFilter(button.getAttribute('data-city-filter'));
    });
  });

  applyFilter('全部');
})();
</script>