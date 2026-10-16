---
layout: page
title: Research
permalink: /research/
---
<div class="cards">
{% for p in site.data.research %}
  <article class="card">
    {% if p.image %}<img class="card-img" src="{{ p.image | relative_url }}" alt="">{% else %}<div class="card-img ph ph-pink"></div>{% endif %}
    <h2 class="item-title">{{ p.title }}</h2>
    {% if p.current %}<p class="eyebrow">In progress</p>{% elsif p.date_label %}<p class="eyebrow">{{ p.date_label }}</p>{% endif %}
    {% for link in p.links %}<a class="more" href="{{ link.url }}">{{ link.title }} →</a>{% endfor %}
  </article>
{% endfor %}
</div>
