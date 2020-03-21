---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles"

layouts_gallery:
  - url: https://beltus.github.io/vision/ml/
    image_path: /images/ml.jpg
  - url: https://beltus.github.io/vision/sc/
    image_path: /images/sc.jpg
---

I present to you the articles I have written so far in diverse topics. Please, take your time to explore which ever suits your needs and then come back to get some more. This is just the beginning. I hope you enjoy reading these...

{% include gallery id="layouts_gallery" class="full" layout="half"%}

<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
