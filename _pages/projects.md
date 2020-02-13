---
layout: archive
title: "Projects"
permalink: /projects/
header:
  image: "/images/projects.jpg"
---
Here is an introduction to some of the projects I have been able to go through over the past months.
For more information visit my github page for codes

## Latest Projects

<div class="grid__wrapper">
  {% assign collection = 'projects' %}
  {% assign collection = 'projects' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
