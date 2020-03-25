---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles"
header:
     image: "https://beltus.github.io/vision/images/galax_article.jpg"
layouts_gallery:
  - url: https://beltus.github.io/vision/ml/
    image_path: /images/ml.jpg
  - url: https://beltus.github.io/vision/sc/
    image_path: /images/sc.jpg
---

I present to you the articles I have written so far in diverse topics. For easy accessibility, the articles have been grouped into different categories - click to open any category of your choice. Take your time to explore which ever suits your needs and then come back to get some more. I hope you enjoy reading these...

## Articles Grouped by Category

{% include gallery id="layouts_gallery" class="full" layout="half"%}

## List of all Articles
List of all the articles in this blog is provided below.

<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
