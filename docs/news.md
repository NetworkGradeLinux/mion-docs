<!-- ---
layout: default
title: News
nav_order: 2
permalink: /news
---

# News

---


{% for post in site.posts %}
<h2>{{ post.title }}<span class="h2-date"> - {{ post.date | date_to_string }}</span></h2>
<a href="{{ post.url }}">Read more...</a>
{% endfor %} -->
