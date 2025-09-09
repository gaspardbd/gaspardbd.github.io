---
layout: bib
title: publications
permalink: /publications/
nav: true
nav_order: 4
---

{% assign default_query = site.scholar.query | default: "@*" %}
{% bibliography --query default_query %}
