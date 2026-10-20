---
layout: page
title: Research
permalink: /research/
---
<div class="cards">
{% assign ongoing_projects = site.data.research | where: 'current', true %}
{% assign past_projects = site.data.research | where_exp: 'project', 'project.current != true' | sort: 'date' | reverse %}
{% assign projects = ongoing_projects | concat: past_projects %}
{% for p in projects %}
  <article class="card">
    {% if p.image %}<img class="card-img{% if p.image_fit == 'contain' %} card-img--contain{% endif %}" src="{{ p.image | relative_url }}" alt="">{% else %}<div class="card-img ph ph-pink"></div>{% endif %}
    <h2 class="item-title">{{ p.title }}</h2>
    {% if p.current %}<p class="eyebrow">In progress</p>{% elsif p.date_label %}<p class="eyebrow">{{ p.date_label }}</p>{% endif %}
    {% for link in p.links %}<a class="more" href="{{ link.url }}">{{ link.title }} →</a>{% endfor %}
  </article>
{% endfor %}
</div>
