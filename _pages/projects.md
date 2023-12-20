---
layout: home
title:  "Projects"
permalink: /projects/
author_profile: true
---

{% assign sorted_projects = site.projects | sort: 'date' %}
{% for project in sorted_projects %}
  <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
  <p><strong>{{ project.date | date: "%B %d, %Y" }}</strong><br>
  {{ project.excerpt }}</p>
{% endfor %}
