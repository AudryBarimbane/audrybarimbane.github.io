---
layout: page
title: Parcours
permalink: /learning-paths/
---

{% for t in site.data.tracks %}
## {{ t.title }}

{{ t.description }} *(source : {{ t.source }})*

{% assign lessons = site.lessons | where: "track", t.id | sort: "order" %}
{% assign total = 0 %}
{% for l in lessons %}
{% assign total = total | plus: l.minutes %}
- {{ l.order }}. **{{ l.phase }}** · [{{ l.title }}]({{ l.url | relative_url }}) · {{ l.summary }} ({{ l.minutes }} min)
{% endfor %}

*{{ lessons.size }} leçons · {{ total }} minutes*

{% endfor %}