---
title: Publications
layout: page
---

Please find below a list of feature publications from our lab:


{% assign tags = site.tags | sort %}
{% for tag in tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <h4 id="{{ t | downcase }}">{{ t | replace: "_", " " | upcase }}</h4>
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
