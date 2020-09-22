---
title: 2 ASIR (1º)
layout: page
permalink: /2asir1/
---

{% for post in site.categories[2asir1] %}
    <a href="{{ post.url | absolute_url }}">
      {{ post.title }}
    </a>
{% endfor %}
