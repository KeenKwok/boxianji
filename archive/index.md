---
layout: default
title: 演出档案
---

# 演出档案

<div style="
  margin-top:-0.8em;
  margin-bottom:0.8em;
  color:#777;
  font-size:0.9em;
  line-height:1.6;
">
  《拨弦记》收录的弹拨乐演出历史记录。
</div>

<div style="
  margin-bottom:1.4em;
  font-size:0.9em;
">
  <a href="{{ '/attention/' | relative_url }}">← 返回演出情报</a>
</div>

{% assign events = site.data.attention | sort: "date" | reverse %}

<!-- 城市筛选 -->

{% assign cities = events | map: "city" | uniq | sort %}

<div style="
  display:flex;
  flex-wrap:wrap;
  gap:8px;
  margin-bottom:2em;
">

  <button
    class="city-filter active"
    data-city="all"
    onclick="filterArchive('all')">
    全部
  </button>

  {% for city in cities %}
  <button
    class="city-filter"
    data-city="{{ city }}"
    onclick="filterArchive('{{ city }}')">
    {{ city }}
  </button>
  {% endfor %}

</div>

<style>
.city-filter {
  border:1px solid #ddd;
  background:#fff;
  color:#555;
  border-radius:999px;
  padding:5px 13px;
  font-size:0.85em;
  line-height:1.4;
  cursor:pointer;
  -webkit-appearance:none;
}

.city-filter.active {
  background:#222;
  color:#fff;
  border-color:#222;
}
</style>

{% assign current_year = "" %}
{% assign current_month = "" %}

{% for event in events %}

  {% assign event_year = event.date | date: "%Y" %}
  {% assign event_month = event.date | date: "%m" %}

  {% if event_year != current_year %}
    {% assign current_year = event_year %}
    {% assign current_month = "" %}

    <div
      class="archive-year"
      data-year="{{ event_year }}"
      style="
        margin-top:2.2em;
        margin-bottom:0.5em;
      ">
      <h2 style="margin-bottom:0;">
        {{ event_year }}
      </h2>
    </div>

  {% endif %}

  {% if event_month != current_month %}

    {% assign current_month = event_month %}

    <div
      class="archive-month"
      data-year="{{ event_year }}"
      data-month="{{ event_month }}"
      style="
        margin-top:1.2em;
        margin-bottom:0.25em;
      ">

      <h3
        class="month-title"
        style="
          margin-bottom:0;
          font-size:1.05em;
          font-weight:600;
        ">
        <span class="month-name">
          {{ current_month | plus: 0 }}月
        </span>
        <span class="month-count"></span>
      </h3>

    </div>

  {% endif %}

  <div
    class="archive-event"
    data-year="{{ event_year }}"
    data-month="{{ event_month }}"
    data-city="{{ event.city }}"
    style="
      margin:0.75em 0 0.75em 14px;
    ">

    <div style="
      line-height:1.35;
      margin-bottom:2px;
    ">
      <strong>
        🎫 {{ event.date | date: "%m.%d" }}｜{{ event.city }}
      </strong>

      <small>
        ｜<a href="{{ event.link }}">查看详情 ↗</a>
      </small>
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

{% endfor %}

<script>

function filterArchive(city) {

  /* 更新胶囊状态 */

  document.querySelectorAll('.city-filter').forEach(function(button) {
    button.classList.remove('active');
  });

  var activeButton = document.querySelector(
    '.city-filter[data-city="' + city + '"]'
  );

  if (activeButton) {
    activeButton.classList.add('active');
  }

  /* 筛选演出 */

  document.querySelectorAll('.archive-event').forEach(function(event) {

    if (city === 'all' || event.dataset.city === city) {
      event.style.display = '';
    } else {
      event.style.display = 'none';
    }

  });

  /* 重新计算每个月的数量 */

  document.querySelectorAll('.archive-month').forEach(function(month) {

    var year = month.dataset.year;
    var monthNumber = month.dataset.month;

    var events = document.querySelectorAll(
      '.archive-event[data-year="' +
      year +
      '"][data-month="' +
      monthNumber +
      '"]'
    );

    var visibleCount = 0;

    events.forEach(function(event) {

      if (event.style.display !== 'none') {
        visibleCount++;
      }

    });

    var countElement = month.querySelector('.month-count');

    if (visibleCount > 0) {

      countElement.textContent =
        ' · ' + visibleCount + '场';

      month.style.display = '';

    } else {

      countElement.textContent = '';
      month.style.display = 'none';

    }

  });

  /* 隐藏没有内容的年份 */

  document.querySelectorAll('.archive-year').forEach(function(yearElement) {

    var year = yearElement.dataset.year;

    var visibleMonths = document.querySelectorAll(
      '.archive-month[data-year="' + year + '"]'
    );

    var hasVisibleMonth = false;

    visibleMonths.forEach(function(month) {

      if (month.style.display !== 'none') {
        hasVisibleMonth = true;
      }

    });

    yearElement.style.display =
      hasVisibleMonth ? '' : 'none';

  });

}


/* 初始状态 */

document.addEventListener('DOMContentLoaded', function() {

  document.querySelectorAll('.archive-month').forEach(function(month) {

    var year = month.dataset.year;
    var monthNumber = month.dataset.month;

    var events = document.querySelectorAll(
      '.archive-event[data-year="' +
      year +
      '"][data-month="' +
      monthNumber +
      '"]'
    );

    var countElement = month.querySelector('.month-count');

    countElement.textContent =
      ' · ' + events.length + '场';

  });

});

</script>