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

<div id="archive-city-filter" style="
  display:flex;
  flex-wrap:wrap;
  gap:6px;
  margin:10px 0 2em;
">

  <button
    type="button"
    data-city-filter="全部"
    class="archive-city-button active"
  >
    全部
  </button>

</div>

<style>

.archive-city-button {
  border:1px solid #ddd;
  border-radius:16px;
  padding:5px 11px;
  background:#fff;
  color:#555;
  font-size:0.78em;
  line-height:1.2;
  cursor:pointer;
  -webkit-appearance:none;
}

.archive-city-button.active {
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
  style="
    margin-top:1.2em;
    margin-bottom:0.25em;
    font-size:1.05em;
    font-weight:600;
  "
>
  {{ current_month | plus: 0 }}月 · {{ month_count }}场
</h3>

{% endif %}


<div
  class="archive-event"
  data-year="{{ event_year }}"
  data-month="{{ event_month }}"
  data-city="{{ event.city | escape }}"
  style="
    margin:0.75em 0 0.75em 14px;
  "
>

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

(function () {

  var filterBox =
    document.getElementById('archive-city-filter');

  if (!filterBox) return;


  /* =========================
     获取全部演出
     ========================= */

  var events =
    document.querySelectorAll('.archive-event');

  var cities = [];


  /* =========================
     收集城市
     ========================= */

  events.forEach(function (event) {

    var city =
      event.getAttribute('data-city');

    if (
      city &&
      cities.indexOf(city) === -1
    ) {
      cities.push(city);
    }

  });


  /* =========================
     按中文城市名称首字母排序
     与 /attention/ 保持一致
     ========================= */

  cities.sort(function (a, b) {

    return a.localeCompare(
      b,
      'zh-CN'
    );

  });


  /* =========================
     创建城市按钮
     ========================= */

  cities.forEach(function (city) {

    var button =
      document.createElement('button');

    button.type = 'button';

    button.textContent = city;

    button.setAttribute(
      'data-city-filter',
      city
    );

    button.className =
      'archive-city-button';

    filterBox.appendChild(button);

  });


  var buttons =
    filterBox.querySelectorAll(
      '.archive-city-button'
    );


  /* =========================
     应用城市筛选
     ========================= */

  function applyFilter(city) {


    events.forEach(function (event) {

      var eventCity =
        event.getAttribute('data-city');

      if (
        city === '全部' ||
        eventCity === city
      ) {

        event.style.display = '';

      } else {

        event.style.display = 'none';

      }

    });


    /* =========================
       更新城市按钮状态
       ========================= */

    buttons.forEach(function (button) {

      var isActive =
        button.getAttribute(
          'data-city-filter'
        ) === city;

      if (isActive) {

        button.classList.add('active');

      } else {

        button.classList.remove('active');

      }

    });


    /* =========================
       更新月份场次
       ========================= */

    document.querySelectorAll(
      '.archive-month'
    ).forEach(function (month) {

      var year =
        month.getAttribute('data-year');

      var monthNumber =
        month.getAttribute('data-month');


      var monthEvents =
        document.querySelectorAll(
          '.archive-event[data-year="' +
          year +
          '"][data-month="' +
          monthNumber +
          '"]'
        );


      var visibleCount = 0;


      monthEvents.forEach(function (event) {

        if (
          event.style.display !== 'none'
        ) {
          visibleCount++;
        }

      });


      if (visibleCount > 0) {

        month.style.display = '';

        month.textContent =
          parseInt(monthNumber, 10) +
          '月 · ' +
          visibleCount +
          '场';

      } else {

        month.style.display = 'none';

      }

    });


    /* =========================
       更新年份显示
       ========================= */

    document.querySelectorAll('h2').forEach(
      function (yearTitle) {

        var year =
          yearTitle.textContent.trim();

        if (!/^\d{4}$/.test(year)) {
          return;
        }


        var months =
          document.querySelectorAll(
            '.archive-month[data-year="' +
            year +
            '"]'
          );


        var hasVisibleMonth = false;


        months.forEach(function (month) {

          if (
            month.style.display !== 'none'
          ) {
            hasVisibleMonth = true;
          }

        });


        if (hasVisibleMonth) {

          yearTitle.style.display = '';

        } else {

          yearTitle.style.display = 'none';

        }

      }
    );

  }


  /* =========================
     绑定城市按钮
     ========================= */

  buttons.forEach(function (button) {

    button.addEventListener(
      'click',
      function () {

        applyFilter(
          button.getAttribute(
            'data-city-filter'
          )
        );

      }
    );

  });


  /* =========================
     默认显示全部
     ========================= */

  applyFilter('全部');

})();

</script>