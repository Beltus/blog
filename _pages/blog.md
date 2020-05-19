---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles"
header:
     image: "https://cdn-images-1.medium.com/max/800/1*dJevYvXpMboY7_OlYmNWQw.jpeg"
layouts_gallery:
  - url: https://beltus.github.io/vision/ml/
    image_path: https://cdn-images-1.medium.com/max/800/1*2TOOMsFHjdPv0FGnvLF-hQ.jpeg
  - url: https://beltus.github.io/vision/sc/
    image_path: https://cdn-images-1.medium.com/max/800/1*rGWbXgg85MG50_OPeoyWiQ.jpeg
---

I present to you the articles I have written so far in diverse topics. For easy accessibility, the articles have been grouped into different categories - click to open any category of your choice. Take your time to explore which ever suits your needs and then come back to get some more. I hope you enjoy reading these...

## Articles Grouped by Category

<div class = "grid__wrapper">
{% include gallery id="layouts_gallery" class="full" layout="half"%}
</div>

## List of all Articles
List of all the articles in this blog is provided below.

<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

## Articles Grouped by Category

<div class = "grid__wrapper">
{% include gallery id="layouts_gallery" class="full" layout="half"%}
</div>

<!-- Begin Mailchimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/horizontal-slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; width:100%;}
	/* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="https://github.us4.list-manage.com/subscribe/post?u=ca4847e09fa3eca66eff34e12&amp;id=cf9e9cda45" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<label for="mce-EMAIL">Subscribe to stay updated!</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="Email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_ca4847e09fa3eca66eff34e12_cf9e9cda45" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>

<!--End mc_embed_signup-->
