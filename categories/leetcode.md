---
layout: default
title: Leetcode
permalink: /categories/leetcode/
---

<h1>Leetcode</h1>
<p>Problem breakdowns, patterns, and approaches.</p>

<ul class="post-list">
  {% assign posts = site.categories.leetcode %}
  {% if posts and posts.size > 0 %}
    {% for post in posts %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span></li>
    {% endfor %}
  {% else %}
    <li>No posts here yet. Stay tuned.</li>
  {% endif %}
</ul>
