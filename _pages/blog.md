---
layout: archive
permalink: /blog/
author_profile: true
title: "List of Articles"
header:
     image: "https://cdn-images-1.medium.com/max/800/1*dJevYvXpMboY7_OlYmNWQw.jpeg"
layouts_gallery:
  - url: https://beltus.github.io/vision/sc/
    image_path: https://cdn-images-1.medium.com/max/800/1*btSkbsTKQSgTciaJBWL8xw.png
  - url: https://beltus.github.io/vision/ml/
    image_path: https://cdn-images-1.medium.com/max/800/1*2TOOMsFHjdPv0FGnvLF-hQ.jpeg
---

I have only 2 things I can offer you on this blog.  
1. If you're interested in becoming the best version of yourself through continuous self-improvement, then I got you.

2. If you have even the tiniest curiosity for Artificial Intelligence and Machine learning related concepts, then you're at the right place.

## Articles Grouped by Category

<div class = "grid__wrapper">
{% include gallery id="layouts_gallery" class="full" layout="half"%}
</div>

## List of all Articles
List of all the articles in this blog is provided below.


<script id="mcjs">!function(c,h,i,m,p){m=c.createElement(h),p=c.getElementsByTagName(h)[0],m.async=1,m.src=i,p.parentNode.insertBefore(m,p)}(document,"script","https://chimpstatic.com/mcjs-connected/js/users/af24155f302fd6d6bb6913dc9/39a2cace563d54e7d3d151992.js");</script>


<div class="grid__wrapper">
  {% assign collection = 'blog' %}
  {% assign posts = site[collection] | reverse %}
  {% for post in posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
<!-- Begin Mailchimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/horizontal-slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; width:100%;}
	/* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="https://github.us18.list-manage.com/subscribe/post?u=af24155f302fd6d6bb6913dc9&amp;id=7833f07b03" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<label for="mce-EMAIL">Join me let's grow together!</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="Email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_af24155f302fd6d6bb6913dc9_7833f07b03" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>

<!-- End Mailchimp Signup Form -->
