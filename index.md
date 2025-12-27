---
layout: default
title: Welcome to my blog
---

<div class="hero">
	<p class="eyebrow">Building in public</p>
	<h1>Engineer, learner, note-taker.</h1>
	<p class="lede">I write concise, practical notes about what I'm learning in engineering, architecture, and tooling.</p>
	<div class="stack-banner">
		<span class="stack-label">Core stack</span>
		<ul class="stack-list">
			<li>Python</li>
			<li>React</li>
			<li>Next.js</li>
			<li>Vue.js</li>
			<li>Node.js</li>
			<li>PostgreSQL</li>
			<li>SQL</li>
		</ul>
	</div>
	<div class="hero-actions">
		<a class="primary-button" href="#posts">Read recent posts</a>
		<a class="ghost-button" href="#about">About me</a>
	</div>
</div>

<section class="section" id="posts">
	<div class="section-header">
		<h2>Recent writing</h2>
		<p>Fresh takes, experiments, and things I figured out the hard way.</p>
	</div>
	<div class="post-grid">
		{% for post in site.posts limit:3 %}
		<article class="post-card">
			<span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
			<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
			<p>{{ post.excerpt | strip_html | truncate: 140 }}</p>
			<a class="read-more" href="{{ post.url | relative_url }}">Read more →</a>
		</article>
		{% endfor %}
	</div>
</section>

<section class="section" id="categories">
	<div class="section-header">
		<h2>Topics</h2>
		<p>Jump to the areas you care about.</p>
	</div>
	<div class="category-grid">
		<a class="category-card" href="{{ "/categories/backend/" | relative_url }}">
			<h3>Backend</h3>
			<p>Services, APIs, databases, and reliability.</p>
		</a>
		<a class="category-card" href="{{ "/categories/frontend/" | relative_url }}">
			<h3>Frontend</h3>
			<p>UI patterns, performance, and polish.</p>
		</a>
		<a class="category-card" href="{{ "/categories/devops/" | relative_url }}">
			<h3>DevOps</h3>
			<p>Infra, pipelines, observability, deployments.</p>
		</a>
		<a class="category-card" href="{{ "/categories/leetcode/" | relative_url }}">
			<h3>Leetcode</h3>
			<p>Problem notes, patterns, and approaches.</p>
		</a>
		<a class="category-card" href="{{ "/categories/questions/" | relative_url }}">
			<h3>Questions</h3>
			<p>Open questions and things I'm digging into.</p>
		</a>
	</div>
</section>

<section class="section two-column" id="about">
	<div>
		<h2>About</h2>
		<p>I'm DNK, a builder who likes to document the process. I care about reliable systems, good tooling, and sharing the shortcuts I discover along the way.</p>
		<ul class="pill-list">
			<li>TypeScript</li>
			<li>Node.js</li>
			<li>Cloud</li>
			<li>APIs</li>
			<li>Testing</li>
		</ul>
	</div>
	<div class="callout-card">
		<h3>Now</h3>
		<ul class="tight-list">
			<li>Shipping small utilities and scripts.</li>
			<li>Exploring better developer experience patterns.</li>
			<li>Writing short, practical blog posts.</li>
		</ul>
	</div>
</section>
