---
layout: default
title: Home
---

<style>
  body {
    background-color: #fffcf0;
    font-family: sans-serif;
    line-height: 1.6;
    padding: 20px;
  }
  .tag-cloud {
    margin-bottom: 2rem;
  }
  .tag-item {
    margin-right: 15px;
    text-decoration: none;
    color: #007bff;
  }
  .tag-item:hover {
    text-decoration: underline;
  }
  .post-list {
    list-style-type: disc;
    padding-left: 20px;
  }
  .post-date {
    font-family: monospace;
    margin-right: 10px;
    color: #555;
  }
</style>

<div class="tag-cloud">
  {% assign tags = site.tags | sort %}
  {% for tag in tags %}
    <a href="#{{ tag[0] | slugify }}" class="tag-item">{{ tag[0] }}</a>
  {% endfor %}
</div>

<hr>

<ul class="post-list">
  {% for post in site.posts %}
  <li class="post-entry" data-tags="{{ post.tags | join: ',' }}">
    <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
  {% endfor %}
</ul>

<script>
  // Listen for hash changes (e.g., clicking a tag link)
  window.addEventListener('hashchange', function() {
    const filter = window.location.hash.substring(1);
    const posts = document.querySelectorAll('.post-entry');

    posts.forEach(post => {
      const tags = post.getAttribute('data-tags').split(',');
      if (!filter || tags.includes(filter)) {
        post.style.display = 'list-item';
      } else {
        post.style.display = 'none';
      }
    });
  });

  // Handle initial load if a hash exists
  if (window.location.hash) {
    window.dispatchEvent(new Event('hashchange'));
  }
</script>