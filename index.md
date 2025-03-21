---
layout: default
title: index
---

# blog

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
       <span>{{- post.date | date: site.theme_config.date_format -}}</span>
    </li>
  {% endfor %}
</ul>


# feed

[feed](feed.xml)
