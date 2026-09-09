# boxianji

> 拨弦记｜弹拨乐资讯、音乐分享与知识记录

![Version](https://img.shields.io/badge/version-v1.0.0-success)
![License](https://img.shields.io/badge/license-MIT-blue)
![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-black)

持续记录世界弹拨乐领域值得关注的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

---

### 🌐 网站

[《拨弦记》网站](https://keenkwok.github.io/boxianji/)

[拨弦记｜演出情报](https://keenkwok.github.io/boxianji/attention/)

---

### 项目简介

《拨弦记》记录弹拨乐领域值得关注的艺术节、赛事、学术、乐器制作、非遗、音乐会及人物资讯。

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

数据流向：

`_data/attention.yml` → 演出情报页面 / RSS / JSON