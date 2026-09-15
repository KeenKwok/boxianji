---
layout: default
title: 演出档案
---

# 演出档案

<div style="margin-top:-0.8em;margin-bottom:0.8em;color:#777;font-size:0.9em;line-height:1.6;">
《拨弦记》收录的弹拨乐演出历史记录。
</div>

<div style="margin-bottom:1.4em;font-size:0.9em;">
<a href="{{ '/attention/' | relative_url }}">← 返回演出情报</a>
</div>

{% assign events = site.data.attention | sort: "date" | reverse %}
{% assign cities = events | map: "city" | uniq | sort %}

<div style="display:flex;flex-wrap:wrap;gap:8px;margin-bottom:2em;">

<button class="city-filter active" data-city="all" onclick="filterArchive('all')">全部</button>

{% for city in cities %}
<button class="city-filter" data-city="{{ city }}" onclick="filterArchive('{{ city }}')">{{ city }}</button>
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

## {{ event_year }}

{% endif %}

{% if event_month != current_month %}

{% assign current_month = event_month %}
{% assign month_count = 0 %}

{% for count_event in events %}
{% assign count_year = count_event.date | date: "%Y" %}
{% assign count_month = count_event.date | date: "%m" %}

{% if count_year == current_year and count_month == current_month %}
{% assign month_count = month_count | plus: 1 %}
{% endif %}

{% endfor %}

<h3
  class="archive-month"
  data-year="{{ event_year }}"
  data-month="{{ event_month }}"
  style="margin-top:1.2em;margin-bottom:0.25em;font-size:1.05em;font-weight:600;">
  {{ current_month | plus: 0 }}月 · {{ month_count }}场
</h3>

{% endif %}

<div
  class="archive-event"
  data-year="{{ event_year }}"
  data-month="{{ event_month }}"
  data-city="{{ event.city }}"
  style="margin:0.75em 0 0.75em 14px;">

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

<script>
function filterArchive(city) {

  /* 更新城市胶囊 */

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


  /* 重新计算每个月的场数 */

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


    /* 有演出：显示月份并更新场数 */

    if (visibleCount > 0) {

      month.style.display = '';

      month.textContent =
        parseInt(monthNumber, 10) +
        '月 · ' +
        visibleCount +
        '场';

    }


    /* 没有演出：隐藏月份 */

    else {

      month.style.display = 'none';

    }

  });


  /* 隐藏没有任何月份的年份 */

  document.querySelectorAll('h2').forEach(function(yearTitle) {

    var year = yearTitle.textContent.trim();

    if (!/^\d{4}$/.test(year)) {
      return;
    }

    var months = document.querySelectorAll(
      '.archive-month[data-year="' + year + '"]'
    );

    var hasVisibleMonth = false;

    months.forEach(function(month) {

      if (month.style.display !== 'none') {
        hasVisibleMonth = true;
      }

    });

    if (hasVisibleMonth) {
      yearTitle.style.display = '';
    } else {
      yearTitle.style.display = 'none';
    }

  });

}
</script>