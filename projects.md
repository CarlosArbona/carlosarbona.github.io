---
layout: page
title: Projects
permalink: /projects/
---

<style>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
  list-style: none;
  padding: 0;
}

.project-card {
  border: 1px solid #e1e4e8;
  border-radius: 8px;
  padding: 1.5rem;
  transition: box-shadow 0.2s ease, transform 0.2s ease;
  background: white;
}

.project-card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  transform: translateY(-2px);
}

.project-name {
  font-size: 1.25rem;
  margin: 0 0 0.5rem 0;
  font-weight: 600;
}

.project-name a {
  text-decoration: none;
  color: #0366d6;
}

.project-name a:hover {
  text-decoration: underline;
}

.project-status {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  font-size: 0.85rem;
  font-weight: 500;
  margin-bottom: 1rem;
}

.status-active { background: #d4edda; color: #155724; }
.status-in-progress { background: #fff3cd; color: #856404; }
.status-prototype { background: #cfe2ff; color: #084298; }
.status-archived { background: #f8d7da; color: #721c24; }
.status-paused { background: #e2e3e5; color: #383d41; }

.project-description {
  color: #586069;
  font-size: 0.95rem;
  line-height: 1.5;
  margin: 0;
}
</style>

<p>A collection of projects I'm currently working on and maintaining.</p>

{% if site.data.projects and site.data.projects.size > 0 %}
<ul class="projects-grid">
  {% for p in site.data.projects %}
  <li class="project-card">
    <h3 class="project-name">
      {% if p.link %}
        <a href="{{ p.link }}" target="_blank" rel="noopener">{{ p.name }}</a>
      {% else %}
        {{ p.name }}
      {% endif %}
    </h3>
    {% assign status_slug = p.status | default: "unknown" | downcase | replace: " ", "-" %}
    <span class="project-status status-{{ status_slug }}">{{ p.status | default: "Unknown" }}</span>
    {% if p.description %}
      <p class="project-description">{{ p.description }}</p>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% else %}
<p>No projects listed yet. Add them to <code>_data/projects.yml</code> or edit this page to add static entries.</p>
{% endif %}
