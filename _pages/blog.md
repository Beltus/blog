---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles Organised by Topics"
---

{% include gallery id="layouts_gallery" class="full" layout="half" %}

For over 20 years, I have been continuously consuming contents from thousand of sources. I asked myself, How much more do I need to consume before convincing myself its time to share my knowledge to the world?. When is the right time? I have decided to begin a new journey in my career and life to be a source of knowledge in the world among the million of sources through this blog and I will like you to take a walk with me and to permit me share my knowledge with you through a series of captivating up-to-date articles I have written and will constantly be writing based on knowledge and my life-experiences.

<br>

I present to you the articles I have written so far in diverse topics. Please, take your time to explore which ever suits your needs and then come back to get some more. This is just the beginning. I hope you enjoy reading these...

<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
