---
title: losiu.org
---

# pages
- On me and this site: [about](/about)

# blog
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
       <span style="font-size:smaller;">{{- post.date | date: site.theme_config.date_format -}}</span>
    </li>
  {% endfor %}
</ul>


# feed
- If you have a RSS reader, subscribe: [feed](feed.xml)

