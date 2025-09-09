---
layout: page
title: projects
permalink: /projects/
nav: true
nav_order: 3
---

<div class="projects">
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in site.projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
</div>
