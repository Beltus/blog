---
title: "Scholarship Related Articles"
layout: single
permalink: /sc/
author_profile: true
header:
  image: 'https://beltus.github.io/vision/assets/images/sc_long.jpg'

entries_layout: grid
classes: wide
---

In this page, you will find a list all the articles related to scholarship applications and educational life of students. I hope this helps you to achieve your dreams. Have fun reading and don't forget to come back for more...


<div class="grid__wrapper">
  {% assign collection = 'sc' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
