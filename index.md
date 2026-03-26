---
layout: default
title: Home
---

<header style="margin-bottom: 40px;">
  <h1 style="font-size: 2.2em; margin-bottom: 0.5rem;">{{ site.title | default: "My Digital Garden" }}</h1>
  
  <input type="text" id="searchInput" placeholder="Search posts or tags..." 
         style="width: 100%; padding: 12px; font-size: 1rem; border: 1px solid #ccc; border-radius: 8px; background: #fffdf5; box-sizing: border-box; margin-bottom: 20px;">

  <div class="tag-cloud" style="font-size: 0.9em; color: #666;">
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      <a href="#{{ tag[0] | slugify }}" class="tag-item" style="margin-right: 12px; color: #007bff;">#{{ tag[0] }}</a>
    {% endfor %}
    <a href="#" class="tag-item" style="color: #666; font-style: italic;">(clear)</a>
  </div>
</header>

<hr style="border: 0; border-top: 1px solid #eee; margin: 20px 0;">

<ul class="post-list" id="postList" style="list-style-type: disc; padding-left: 20px;">
  {% for post in site.posts %}
  <li class="post-entry" data-title="{{ post.title | downcase }}" data-tags="{{ post.tags | join: ',' | downcase }}">
    <span class="post-date" style="font-family: monospace; color: #777; margin-right: 10px;">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
  {% endfor %}
</ul>

<script>
  const searchInput = document.getElementById('searchInput');
  const posts = document.querySelectorAll('.post-entry');

  function filterPosts() {
    const searchTerm = searchInput.value.toLowerCase();
    const hashTag = window.location.hash.substring(1).toLowerCase();

    posts.forEach(post => {
      const title = post.getAttribute('data-title');
      const tags = post.getAttribute('data-tags');
      
      const matchesSearch = title.includes(searchTerm) || tags.includes(searchTerm);
      const matchesHash = !hashTag || tags.includes(hashTag);

      if (matchesSearch && matchesHash) {
        post.style.display = 'list-item';
      } else {
        post.style.display = 'none';
      }
    });
  }

  searchInput.addEventListener('input', filterPosts);
  window.addEventListener('hashchange', filterPosts);
  if (window.location.hash) filterPosts();
</script>
