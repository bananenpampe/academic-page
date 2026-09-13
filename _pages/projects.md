---
layout: page
title: projects
permalink: /projects/
description: My three main research themes. Each page has a comment section, so feel free to start a discussion!
nav: true
nav_order: 2
horizontal: false
# Card layout: same image height everywhere so titles line up, a light divider
# between thumbnail and text, and the GitHub link pinned to the lower-left corner.
_styles: >
  .projects .card figure { margin: 0; padding: 0.75rem; border-bottom: 1px solid var(--global-divider-color); }
  .projects .card-img-top { height: 200px; object-fit: contain; object-position: center; }
  .projects .card .card-body { display: flex; flex-direction: column; }
  .projects .card .card-body > .row { margin-top: auto; padding-top: 0.75rem; }
---

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
