---
layout: default
title: DevOps
permalink: /categories/devops/
---

<h1>DevOps</h1>
<p>Infra, pipelines, observability, deployments, and tooling.</p>

<ul class="post-list">
  {% assign posts = site.categories.devops %}
  {% if posts and posts.size > 0 %}
    {% for post in posts %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span></li>
    {% endfor %}
  {% else %}
    <li>No posts here yet. Stay tuned.</li>
  {% endif %}
</ul>
