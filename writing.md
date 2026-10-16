---
layout: page
title: Writing
permalink: /writing/
intro: Blog posts, op-eds, and other public writing.
---
{% assign items = site.data.writing | sort: 'date' | reverse %}
{% if items.size == 0 %}
<p class="empty">Writing will be listed here.</p>
{% else %}
<div class="rows">
{% for w in items %}
  <a class="row" href="{{ w.url }}" target="_blank" rel="noopener">
    {% include thumb.html image=w.image tint="pink" %}
    <span class="row-text">
      <span class="eyebrow">{{ w.outlet }} · {{ w.date | date: '%B %Y' }}</span>
      <span class="row-title">{{ w.title }}</span>
    </span>
    <span class="arrow" aria-hidden="true">→</span>
  </a>
{% endfor %}
</div>
{% endif %}
