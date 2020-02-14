---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles"
---

I present to you the articles I have written so far in diverse topics. Please, take your time to explore which ever suits your needs and then come back to get some more. This is just the beginning. I hope you enjoy reading these...

<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
