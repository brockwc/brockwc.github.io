---
layout: page
title: "Posts by Category"
permalink: /categories/
---

<ul class="post-list">
{% for cat in site.categories %}
  {% assign name = cat[0] %}
  {% if name != 'jekyll' and name != 'update' %}
  <li>
    <h2>{{ name }}</h2>
    <ul>
      {% for post in cat[1] %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </li>
      {% endfor %}
    </ul>
  </li>
  {% endif %}
{% endfor %}
</ul>
