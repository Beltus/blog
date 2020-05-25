---
layout: archive
title: "Projects"
permalink: /projects/
header:
  image: "https://cdn-images-1.medium.com/max/800/1*fDjB0qHOLNYAOldppdoMRg.jpeg"
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
