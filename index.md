---
layout: default
title: Home
---

<style>
  #postList {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .home-title {
    font-size: clamp(1.6rem, 5vw, 2.2em);
    margin-bottom: 0.5rem;
  }

  .post-item {
    margin-bottom: 12px;
    display: flex;
    flex-wrap: wrap;
    align-items: baseline;
    gap: 4px 0;
  }

  .post-date {
    font-family: monospace;
    color: var(--muted-soft);
    margin-right: 15px;
    flex-shrink: 0;
  }

  .post-tags {
    font-size: 0.78em;
    color: var(--muted-soft);
    margin-left: 10px;
  }

  .post-tags span {
    margin-right: 6px;
  }

  .year-nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 8px;
    font-family: monospace;
    color: var(--muted-soft);
  }

  .year-nav a {
    min-height: 40px;
    display: inline-flex;
    align-items: center;
  }

  .year-nav .year-current {
    font-size: 1.1em;
    color: var(--muted-soft);
  }

  .year-nav .year-link.is-disabled {
    visibility: hidden;
    pointer-events: none;
  }

  .year-section {
    display: none;
  }

  .year-section.is-active {
    display: block;
  }

  .month-section {
    margin-bottom: 28px;
  }

  .month-heading {
    font-family: monospace;
    font-size: 0.95em;
    font-weight: normal;
    color: var(--muted-soft);
    margin: 0 0 12px 0;
    padding-bottom: 6px;
    border-bottom: 1px solid var(--border);
  }

  .month-section.is-empty {
    display: none;
  }

  .tag-cloud {
    font-size: 0.9em;
    color: var(--muted);
    display: flex;
    flex-wrap: wrap;
    gap: 8px 12px;
  }

  .tag-cloud .tag-item.is-clear {
    color: var(--muted);
    font-style: italic;
  }

  @media (max-width: 560px) {
    .post-date {
      width: 100%;
      margin-right: 0;
      margin-bottom: 2px;
    }

    .post-tags {
      margin-left: 0;
      width: 100%;
    }
  }
</style>

<header style="margin-bottom: 40px;">
  <h1 class="home-title">{{ site.title | default: "My Digital Garden" }}</h1>

  <input type="text" id="searchInput" class="search-input" placeholder="Search posts or tags...">

  <div class="tag-cloud">
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      <a href="#{{ tag[0] | slugify }}" class="tag-item">#{{ tag[0] }}</a>
    {% endfor %}
    <a href="#" class="tag-item is-clear">(clear)</a>
  </div>
</header>

{% assign years = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% assign year_list = "" | split: "," %}
{% for year_group in years %}
  {% assign year_list = year_list | push: year_group.name %}
{% endfor %}
{% assign latest_year = year_list | first %}

<nav class="year-nav" id="yearNav" aria-label="Posts by year">
  <a href="#" class="year-link year-prev" id="yearPrev">‹ <span></span></a>
  <span class="year-current" id="yearCurrent">{{ latest_year }}</span>
  <a href="#" class="year-link year-next" id="yearNext"><span></span> ›</a>
</nav>

<hr class="site-rule">

<div id="postList">
  {% for year_group in years %}
  <section class="year-section{% if year_group.name == latest_year %} is-active{% endif %}" data-year="{{ year_group.name }}">
    {% assign months = year_group.items | group_by_exp: "post", "post.date | date: '%Y-%m'" %}
    {% for month_group in months %}
    <section class="month-section" data-month="{{ month_group.name }}">
      <h2 class="month-heading">{{ month_group.items.first.date | date: "%B %Y" }}</h2>
      <ul style="list-style: none; padding: 0; margin: 0;">
        {% for post in month_group.items %}
        <li class="post-item" data-title="{{ post.title | downcase }}" data-tags="{{ post.tags | join: ',' | downcase }}">
          <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{ post.url }}">{{ post.title }}</a>
          {% assign visible_tags = post.tags | reject: "publish" %}
          {% if visible_tags.size > 0 %}
          <span class="post-tags">{% for tag in visible_tags %}<span>#{{ tag }}</span>{% endfor %}</span>
          {% endif %}
        </li>
        {% endfor %}
      </ul>
    </section>
    {% endfor %}
  </section>
  {% endfor %}
</div>

<script>
  const searchInput = document.getElementById('searchInput');
  const yearSections = Array.from(document.querySelectorAll('.year-section'));
  const yearOrder = yearSections.map(section => section.dataset.year);
  const yearCurrent = document.getElementById('yearCurrent');
  const yearPrev = document.getElementById('yearPrev');
  const yearNext = document.getElementById('yearNext');
  const posts = document.querySelectorAll('.post-item');
  const monthSections = document.querySelectorAll('.month-section');

  let activeYear = yearOrder[0] || null;
  let searchMode = false;

  function setActiveYear(year) {
    activeYear = year;
    yearSections.forEach(section => {
      section.classList.toggle('is-active', searchMode || section.dataset.year === year);
    });
    if (yearCurrent) yearCurrent.textContent = year;

    const index = yearOrder.indexOf(year);
    const hasPrev = index > 0;
    const hasNext = index >= 0 && index < yearOrder.length - 1;

    yearPrev.classList.toggle('is-disabled', !hasPrev);
    yearNext.classList.toggle('is-disabled', !hasNext);
    yearPrev.querySelector('span').textContent = hasPrev ? yearOrder[index - 1] : '';
    yearNext.querySelector('span').textContent = hasNext ? yearOrder[index + 1] : '';
  }

  function updateMonthVisibility() {
    monthSections.forEach(section => {
      const visiblePosts = section.querySelectorAll('.post-item:not([style*="display: none"])');
      section.classList.toggle('is-empty', visiblePosts.length === 0);
    });
  }

  function filterPosts() {
    const searchTerm = searchInput.value.toLowerCase().trim();
    const hashTag = window.location.hash.substring(1).toLowerCase();
    searchMode = Boolean(searchTerm || hashTag);

    posts.forEach(post => {
      const title = post.getAttribute('data-title') || '';
      const tags = post.getAttribute('data-tags') || '';

      const matchesSearch = !searchTerm || title.includes(searchTerm) || tags.includes(searchTerm);
      const matchesHash = !hashTag || tags.includes(hashTag);

      post.style.display = (matchesSearch && matchesHash) ? 'flex' : 'none';
    });

    yearSections.forEach(section => {
      if (searchMode) {
        const hasVisible = section.querySelector('.post-item:not([style*="display: none"])');
        section.classList.toggle('is-active', Boolean(hasVisible));
      }
    });

    if (!searchMode) setActiveYear(activeYear);
    updateMonthVisibility();

    document.getElementById('yearNav').style.display = searchMode ? 'none' : 'flex';
  }

  function changeYear(dir) {
    const index = yearOrder.indexOf(activeYear);
    const nextIndex = index + dir;
    if (nextIndex < 0 || nextIndex >= yearOrder.length) return;
    setActiveYear(yearOrder[nextIndex]);
    updateMonthVisibility();
  }

  yearPrev.addEventListener('click', (e) => {
    e.preventDefault();
    changeYear(-1); // toward newer years
  });

  yearNext.addEventListener('click', (e) => {
    e.preventDefault();
    changeYear(1); // toward older years
  });

  searchInput.addEventListener('input', filterPosts);
  window.addEventListener('hashchange', filterPosts);

  setActiveYear(activeYear);
  if (window.location.hash || searchInput.value) {
    filterPosts();
  } else {
    updateMonthVisibility();
  }
</script>
