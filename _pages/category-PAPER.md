---
layout: archive
title: "Paper reviews"
permalink: /PAPER/
author_profiles: true
entries_layout: grid
---

{% assign posts = site.categories.PAPER %}
{% for post in posts %} 
  {% include archive-single.html type=page.entries_layout %} 
{% endfor %}
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>