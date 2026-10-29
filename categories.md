
---
layout: page
title: 카테고리
permalink: /categories/
---

공부 분야별로 게시글을 모아 볼 수 있습니다.

{% raw %}{% assign categories = site.categories | sort %}

{% for category in categories %}
## {{ category[0] }}

{% assign posts = category[1] | sort: "date" | reverse %}
{% for post in posts %}
- [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

{% endfor %}{% endraw %}
