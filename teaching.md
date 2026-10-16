---
layout: page
title: Teaching
permalink: /teaching/
---
{% assign items = site.data.teaching | sort: 'date' | reverse %}
<ul class="list">
{% for c in items %}
  <li class="item">
    <span class="eyebrow">{{ c.term }}</span>
    <span class="item-title">{% if c.url %}<a href="{{ c.url }}">{{ c.course | default: c.title }}</a>{% else %}{{ c.course | default: c.title }}{% endif %}</span>
    <span class="meta">{% if c.role %}{{ c.role }} · {% endif %}{{ c.institution }}{% if c.location %} · {{ c.location }}{% endif %}</span>
    {% if c.url %}<a class="more" href="{{ c.url }}">Course details →</a>{% endif %}
  </li>
{% endfor %}
</ul>
