---
layout: page
title: Publications
permalink: /publications/
---
{% assign items = site.data.publications | sort: 'date' | reverse %}
{% if items.size == 0 %}
<p class="empty">Publications will be listed here.</p>
{% else %}
<ul class="list">
{% for p in items %}
  <li class="item">
    <span class="eyebrow">{{ p.type }}{% if p.date %}{% if p.type %} · {% endif %}{{ p.date | date: '%Y' }}{% endif %}</span>
    <span class="item-title">{% if p.url %}<a href="{{ p.url }}">{{ p.title }}</a>{% else %}{{ p.title }}{% endif %}</span>
    <span class="meta">{{ p.authors }}{% if p.venue %}{% if p.authors %} · {% endif %}<em>{{ p.venue }}</em>{% endif %}</span>
    {% if p.role %}<span class="meta">{{ p.role }}</span>{% endif %}
    {% for link in p.links %}<a class="more" href="{{ link.url }}">{{ link.title }} →</a>{% endfor %}
    {% if p.pdf %}<a class="more" href="{{ p.pdf | relative_url }}">PDF</a>{% endif %}
  </li>
{% endfor %}
</ul>
{% endif %}
