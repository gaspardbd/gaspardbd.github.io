---
layout: page
title: projects
permalink: /projects/
nav: true
nav_order: 3
---

<div class="projects">
  <div class="grid">
    <div class="grid-sizer"></div>
    <div class="row">
      {% assign filtered_projects = site.projects %}
      {% assign categorized_projects = filtered_projects | where_exp: 'item', 'item.category != nil' %}
      {% assign uncategorized_projects = filtered_projects | where_exp: 'item', 'item.category == nil' %}

      {% for project in uncategorized_projects %}
        <div class="grid-item">
          {% include projects.liquid %}
        </div>
      {% endfor %}

      {% if site.enable_project_categories and categorized_projects.size > 0 %}
        {% assign grouped = categorized_projects | group_by: 'category' %}
        {% for group in grouped %}
          <h2 class="category">{{ group.name }}</h2>
          {% for project in group.items %}
            <div class="grid-item">
              {% include projects.liquid %}
            </div>
          {% endfor %}
        {% endfor %}
      {% endif %}
    </div>
  </div>
</div>
