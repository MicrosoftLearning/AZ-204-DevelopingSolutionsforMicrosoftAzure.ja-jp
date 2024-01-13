---
title: オンラインでホストされる手順
permalink: index.html
layout: home
---

## コンテンツ ディレクトリ

各ラボへのハイパーリンクを以下に示します。

## ラボ

{% assign labs = site.pages | where_exp: "page", "page.url contains '/Instructions/Labs'" %}
| モジュール | ラボ |
| --- | --- |
{% for activity in labs  %}{% if activity.lab.az204Module %}| {{ activity.lab.az204Module }} | [{{ activity.lab.az204Title }}]({{ site.github.url }}{{ activity.url }}) |
{% endif %}{% endfor %}
