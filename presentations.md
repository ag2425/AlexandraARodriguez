---
layout: page
title: Presentations
permalink: /presentations/
intro: Presentations, workshops, panels, invited talks, and event facilitation.
---
{% assign items = site.data.presentations | sort: 'date' | reverse %}
{% if items.size == 0 %}
<p class="empty">Presentations will be listed here.</p>
{% else %}
<ul class="list">
{% for p in items %}
  <li class="item item-thumb">
    {% include thumb.html image=p.image tint="green" fit=p.image_fit position=p.image_position %}
    <span class="row-text">
      <span class="eyebrow"><span class="tag">{{ p.type }}</span> {% if p.date_label %}{{ p.date_label }}{% else %}{{ p.date | date: '%B %Y' }}{% endif %}</span>
      <span class="item-title">{% if p.url %}<a href="{{ p.url }}">{{ p.title }}</a>{% else %}{{ p.title }}{% endif %}</span>
      {% if p.url %}<a class="more" href="{{ p.url }}">Read more →</a>{% endif %}
      <span class="meta">{{ p.event }}{% if p.location %} · {{ p.location }}{% endif %}</span>
      {% if p.role %}<span class="meta">{{ p.role }}</span>{% endif %}
    </span>
  </li>
{% endfor %}
</ul>
{% endif %}
