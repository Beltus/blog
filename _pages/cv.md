---
title: "Computer Vision"
layout: archive
permalink: /cv/
author_profile: true # set the authors  biography as side nav bar
header:
  image: 'https://beltus.github.io/vision/images/cv_long.jpg'

#sidebar:
  #nav: sidebar-sample
#layout_gallery:
---

I am excited to share with you guys computer vision techniques and projects that will definitely propel your career ladder. Feel free to check out my articles listed below with codes provided on my github page as well.


## Latest Computer Vision Articles

<div class="grid__wrapper">
  {% assign collection = 'cv' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
