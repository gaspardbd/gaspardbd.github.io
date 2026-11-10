---
layout: page
title: projects
permalink: /projects/
nav: true
nav_order: 3
hide_project_images: true
---

<div class="projects">
  {% assign sorted_projects = site.projects | sort: 'importance' %}
  <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% unless project.title == 'GitHub Projects' %}
        {% include projects.liquid %}
      {% endunless %}
    {% endfor %}
  </div>
</div>
