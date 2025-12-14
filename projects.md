---
layout: page
title: Projects
permalink: /projects/
---

A collection of projects I'm currently working on and maintaining. If you'd like to contribute or see more details, click the links.

{% if site.data.projects and site.data.projects.size > 0 %}
<ul class="projects-list">
  {% for p in site.data.projects %}
  <li class="project">
    <h3>
      {% if p.link %}
        <a href="{{ p.link }}" target="_blank" rel="noopener">{{ p.name }}</a>
      {% else %}
        {{ p.name }}
      {% endif %}
    </h3>
    {% if p.description %}
      <p>{{ p.description }}</p>
    {% endif %}
    <p>
      <strong>Status:</strong> {{ p.status | default: "Unknown" }}
      {% if p.tech %}
        • <strong>Tech:</strong> {{ p.tech | join: ", " }}
      {% endif %}
    </p>
    {% if p.repo %}
      <p><a href="{{ p.repo }}" target="_blank" rel="noopener">Repository</a></p>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% else %}
<p>No projects listed yet. Add them to <code>_data/projects.yml</code> or edit this page to add static entries.</p>
{% endif %}
