---
title: Research Items
layout: page
---

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <h4 id="{{ t | downcase }}">{{ t | replace: "_", " " | downcase }}</h4>
  <ul>
  {% for post in posts %}
    {% if post.tags contains t %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span class="date">{{ post.date | date: "%B %-d, %Y"  }}</span>
      </li>
    {% endif %}
  {% endfor %}
  </ul>
{% endfor %}