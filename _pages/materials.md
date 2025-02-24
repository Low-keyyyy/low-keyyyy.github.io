---
layout: materials
permalink: /materials/
title: materials
description: A collection for learning materials. Most are related to CS currently.
nav: true
nav_order: 2
---

---
<ul class="material-list">
  {% assign materialslist = site.materials %}
  {% assign listsize = site.materials | size %}

  <!-- <h1>{{listsize}}</h1>     -->
    
  {% for material in materialslist %} 
  <li>
    {% assign year = post.date | date: "%Y" %}
    {% assign tags = post.tags | join: "" %}
    {% assign categories = post.categories | join: "" %}
    <p>
      <a class="post-title material-name" href="{{ material.redirect | relative_url }}">{{ material.title }}</a>
    </p>
  </li>
  {% endfor %}
</ul>