---
title: 2ASIR1
layout: page
permalink: /2asir1/
---

{% for post in site.categories.2asir1 %}
    <a href="{{ post.url | absolute_url }}">
      {{ post.title }}
    </a>
{% endfor %}

{% for post in site.categories.2asir1 %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
