---
layout: archive
title: "Server"
permalink: /server/
author_profiles: true
entries_layout: list
---

{% assign posts = site.categories.server %}
{% for post in posts %} 
  {% include archive-single-custom.html type=page.entries_layout %} 
{% endfor %}
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>