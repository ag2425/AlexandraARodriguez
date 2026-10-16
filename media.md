---
layout: page
title: Media
permalink: /media/
intro: Interviews, features, and coverage of my work.
---
{% assign dated_items = site.data.media | where_exp: 'item', 'item.date' | sort: 'date' | reverse %}
{% assign undated_items = site.data.media | where_exp: 'item', 'item.date == nil' %}
{% assign items = dated_items | concat: undated_items %}
{% if items.size == 0 %}
<p class="empty">Media will be listed here.</p>
{% else %}
<div class="rows">
{% for w in items %}
  <article class="media-item">
  {% if w.url %}<a class="row" href="{{ w.url | escape }}" target="_blank" rel="noopener">{% else %}<div class="row">{% endif %}
    {% include thumb.html image=w.image tint="brown" %}
    <span class="row-text">
      <span class="eyebrow">{% if w.type %}<span class="tag">{{ w.type }}</span> {% endif %}{{ w.outlet }}{% if w.date_label or w.date %} · {% if w.date_label %}{{ w.date_label }}{% else %}{{ w.date | date: '%B %Y' }}{% endif %}{% endif %}</span>
      <span class="row-title">{{ w.title }}</span>
      {% if w.summary %}<span class="meta">{{ w.summary }}</span>{% endif %}
    </span>
    {% if w.url %}<span class="arrow" aria-hidden="true">→</span></a>{% else %}</div>{% endif %}
    {% if w.links %}
    <div class="media-links">
      {% for link in w.links %}<a class="more" href="{{ link.url | escape }}" target="_blank" rel="noopener">{{ link.title }} →</a>{% endfor %}
    </div>
    {% endif %}
  </article>
{% endfor %}
</div>
{% endif %}
