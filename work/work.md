---
layout: default
title: Work
---

{% for project in site.data.projects %}

    {{ project.name }}
    {{ project.url }}
    {{ project.responsibilities }}
    {{ project.smallimage }}
    
{% endfor %}
