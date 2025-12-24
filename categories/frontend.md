---
layout: default
title: Frontend
permalink: /categories/frontend/
---

<h1>Frontend</h1>
<p>UI patterns, performance notes, and polish.</p>

<ul class="post-list">
  {% assign posts = site.categories.frontend %}
  {% if posts and posts.size > 0 %}
    {% for post in posts %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span></li>
    {% endfor %}
  {% else %}
    <li>No posts here yet. Stay tuned.</li>
  {% endif %}
</ul>
