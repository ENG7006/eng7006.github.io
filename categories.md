---
layout: inner
title: Categories
permalink: /blog/categories/
---

{% capture categories %}{% for category in site.categories %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign category = categories | split:',' | sort %}
{% for item in (0..site.categories.size) %}{% unless forloop.last %}
{% capture word %}{{ category[item] | strip_newlines }}{% endcapture %}
<h3 class="category" id="{{ word }}">{{ word }}</h3>
<ul>
{% for post in site.categories[word] %}{% if post.title != null %}
<li><span>{{ post.date | date: "%b %d" }}</span>: <a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></li>
{% endif %}{% endfor %}
</ul>
{% endunless %}{% endfor %}
<br/><br/>
