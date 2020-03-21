---
title: "Scholarships"
layout: single
permalink: /sc/
author_profile: true
author_profile: False
header:
  image: 'https://beltus.github.io/vision/images/sc_long.jpg'

sidebar:
  nav: sidebar-sample
#layout_gallery:
---

Every time I stumbled across a scholarship opportunity, within the first few minutes of skimming through it, I got freaking overwhelmed by the whole process. The eligibility criteria, the requirements, not leaving out the lengthy essays, man ohh man, it was quite disheartening. Now, imagine you got more than 20 of such applications you got to fill for which each requires this much effort. You will need to muster all the inner-strength you got in you to achieve this. Will it not be relieving if you had a system set up which takes care of all the mundane work necessary for a smooth and stress-free application?

<br>

In this page, I have listed all the articles related to scholarship applications to help students who are struggling like I did which the seemingly arduous and perplexing scholarship application procedure


<div class="grid__wrapper">
  {% assign collection = 'sc' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
