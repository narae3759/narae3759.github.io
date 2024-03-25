---
layout: archive
title: "LaTeX"
permalink: /latex/
author_profiles: true
entries_layout: list
---

{% assign posts = site.categories.latex %}
{% for post in posts %} 
  {% include archive-single-custom.html type=page.entries_layout %} 
{% endfor %}
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>