---
layout: page
title: Policy
permalink: /policy/
---
{% assign items = site.data.presentations | concat: site.data.media | concat: site.data.writing | where: 'policy', true | sort: 'date' | reverse %}
<div class="rows">
{% for item in items %}
  <a class="row" href="{{ item.url | escape }}" target="_blank" rel="noopener">
    {% include thumb.html image=item.image tint="green" fit=item.image_fit position=item.image_position %}
    <span class="row-text">
      <span class="eyebrow">{{ item.type }} · {% if item.date_label %}{{ item.date_label }}{% else %}{{ item.date | date: '%B %Y' }}{% endif %}</span>
      <span class="row-title">{{ item.title }}</span>
      <span class="meta">{{ item.outlet | default: item.event }}</span>
      {% if item.role %}<span class="meta">{{ item.role }}</span>{% endif %}
    </span>
    <span class="arrow" aria-hidden="true">→</span>
  </a>
{% endfor %}
</div>
