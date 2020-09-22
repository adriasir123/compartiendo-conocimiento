---
layout: page
---

{% for post in site.categories[2asir1] %}
    <a href="{{ post.url | absolute_url }}">
      {{ post.title }}
    </a>
{% endfor %}
