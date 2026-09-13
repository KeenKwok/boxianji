# boxianji

> 拨弦记｜弹拨乐资讯、音乐分享与知识记录

![GitHub release](https://img.shields.io/github/v/release/KeenKwok/boxianji)
![GitHub License](https://img.shields.io/github/license/KeenKwok/boxianji)
![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-black)

持续记录世界弹拨乐领域值得关注的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

---

### 🌐 网站

[《拨弦记》网站](https://keenkwok.github.io/boxianji/)

[拨弦记｜演出情报](https://keenkwok.github.io/boxianji/attention/)

---

## 项目简介

《拨弦记》（Boxianji）是一个面向中文用户的弹拨乐开放资讯项目，持续收录世界弹拨乐领域的演出情报、艺术节、赛事、学术、乐器制作、非遗及人物资讯，并通过网站、RSS 与 JSON 开放接口提供长期访问。

其中，「拨弦记｜演出情报」持续收录近期值得关注的弹拨乐演出，并支持按城市快速筛选。

---

## 项目文档

项目的编辑规范、运营流程和长期规划。

- 📘 编辑操作手册 (EDITORIAL.md) *（计划）*
- 🗂️ 数据规范（DATA_SCHEMA.md）*（计划）*
- 🗺️ 开发路线图（ROADMAP.md）*（计划）*

---

## 开放接口

《拨弦记》演出情报提供 RSS 与 JSON 两种开放接口。

### RSS

订阅《拨弦记》近期演出情报：

https://keenkwok.github.io/boxianji/attention.xml

[打开 RSS ↗](https://keenkwok.github.io/boxianji/attention.xml)

### JSON

获取结构化演出数据：

https://keenkwok.github.io/boxianji/attention.json

[打开 JSON ↗](https://keenkwok.github.io/boxianji/attention.json)

### 数据来源

演出情报以仓库中的 `_data/attention.yml` 作为唯一数据源，网站页面、RSS 与 JSON 接口均由该数据源生成。

网站端提供按城市筛选功能；该功能不改变演出数据结构，也不影响 RSS 与 JSON 接口。

数据流向：

`_data/attention.yml` → 演出情报页面 / RSS / JSON

---

## 版本历史

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| v1.2.0 | 2026-09-13 | 新增演出情报城市筛选功能，城市选项根据现有演出数据自动生成；支持近期演出与已结束演出的同步筛选。 |
| v1.0.0 | 2026-09-09 | 首个正式版本，开放演出情报数据库、RSS、JSON 接口、首页演出入口、周报归档。 |