---
layout: materials
permalink: /materials/
title: materials
description: A growing collection of your cool projects.
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
    <h5>
      <a class="post-title" href="{{ material.redirect | relative_url }}">{{ material.title }}</a>
    </h5>
  </li>
  {% endfor %}
</ul>